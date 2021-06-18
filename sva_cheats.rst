
***************************
SVA Cheats for Formal
***************************
This guide is intended as a quick reference guide for SystemVerilog Assertions constructs which can be evaluated efficiently by formal tools. This guide is a recommended subset of the SVA constructs which a formal tool would actually support.


Not Recommend Constructs for Formal
===================================
.. note::
    This is based upon the IEEE 1800-2017 Standard (LRM).
    Refer to “Chapter 16. Assertions” and search for the keywords in ``red``.


``intersect``,         ``throughout``,
``or``,                ``and``,
``within``,            ``expect``,
``first_match()`` ,    Local Variables , 
Immediate Assertions,
``if`` property ``else`` property,
sequence. ``triggered``,
sequence[->N] and
sequence[=N]




Constructs To be Use With Caution
=================================

sequence[*N]

``$past`` (expr, N)

In both cases keep N as small as possible, e.g. below 10.
Recommended to model $past() with Auxiliary
Code instead.




Verification Directives
=======================

.. warning::
    A property declaration is merely a definition of behaviour. Nothing gets checked until we have given a verification directive to the tool which states what should be done with
    that behaviour. All properties must have a clock defined explicitly or via a default clock declaration




.. confval:: Syntax

    label : ``assert property`` (prop_expr)

Directive to the tool to ensure that the property holds, is true, under all circumstances

Example
-------

.. code:: python

      P1_INST : assert property (P1(SIG1, SIG2, S3) );
      P2: assert property ( @(posedge clk) A | -> B );
      P3: assert property ( ERROR_CNT != 10 );
      P1A_INS: assert property(@(posedge clka) (P1A));



.. confval:: Syntax

    label : ``assume property`` (prop_expr)

Directive to the tool to limit the behaviour of the design under test (DUT) inputs to the behaviour specified. Also known as constraints.

Example
-------

.. code:: python

      P4 : assume property (req && !gnt |=> req );
      P5 : assume property ( @(posedge clk3) not (full && empty) );



.. confval:: Syntax

    label : ``cover property`` (prop_expr)

Directive to a formal tool to demonstrate one example of how the sequence can complete given the design and assumptions

Example
-------

.. code:: python

      C1 : cover sequence (full ##[+] empty );
      C2 : cover property (@(posedge clk2) (SEQ1) ) ;


.. note::
      For cover property it is recommended for prop_expr to only be a sequence, i.e. not contain
      implication operators | -> or |=> and the cover directive states cover sequence instead ofcover property

Implication Operators
======================

Implies that either :
1) As a consequence of an enabling condition occurring then a fulfilling condition must occur or the property does not hold.
2) The enabling condition never occurs.

.. confval:: Syntax

    sequence_expr ``|->`` property_expr


Holds under these conditions:
3) Ifsequence_expr completes then
property_expr starts the same cycle and
subsequently completes
4) sequence_expr never completes
.. code:: python

      P6: assert property ( A ##1 B | -> C ##1 D );

P6: assert property ( A ##1 B | -> C ##1 D );
P6 would pass if we observe the sequence :
 ( A ##1 (B && C) ##1 D );


.. confval:: Syntax

    sequence_expr ``|=>`` property_expr


Holds under these conditions:
5) Ifsequence_expr completes then
property_expr starts the next cycle and
subsequently completes
6) sequence_expr never completes

.. code:: python

      P7: assert property ( A ##1 B |=> C ##1 D );


P7 would pass if we observe the sequence :
 ( A ##1 B ##1 C ##1 D );

Recommended not to nest implication operators as it
becomes confusing, for example:

.. code:: python

      P8: assert property ( A |=> B |=> C );


This is exactly the same as:

.. code:: python

      P9: assert property ( A ##1 B |=> C );


P8 or P8_EQUIV wouldn’t fail if we observe the sequence :
 ( A ##1 ! B );


Different Dealys
==================

.. note::
    N and M are constants known at elaboration. M can be the
    symbol $ meaning “infinity”. M>=N. M and N can be 0.




.. confval:: Syntax

    ``##[N:M]`` or ``##N``

Example
-------

.. code:: python

      P1_UNKNONCYC : assert property( A |=> B ##[0:$] C );
      P2_THREECYC: assert property ( A |=> ##3 C );


Disabling Condition
====================

.. confval:: Syntax

    ``disable iff`` (boolean_expr)

.. note::
    If boolean expr is true then all current outstanding
    obligations for that property (including all overlapping ones)
    are removed. For example, if a property requires that if a
    request is seen then eventually a grant is observed then one
    may expect that a reset removes that obligation for the
    expected grant. Upon the next request after the disable we
    then expect an obligation for a future grant.


Example
-------

.. code:: python

      P10: assert property
            ( @(posedge clk) disable iff (!rst_n)
                  req |=> ##[*] gnt );



.. note::
    It may get very tedious if the Boolean_expr required to
    disable a property is the same for many properties. In that
    case a default disable can be defined as a standalone
    statement:

.. confval:: Syntax

    ``default disable iff`` (boolean_expr)


This default disable applies to all properties, in the current
scope only, which do not have an explicit disable iff
defined:

Example
-------

.. code:: python

      default disable iff (CANCEL)
          P11: assert property (
           @(posedge clk) disable iff (!rst_n)
            A |=> B );

          P12: assert property
           ( @(posedge clk) C |=> D );

 P10 is disabled by !rst_n. P11 is disabled by CANCEL
default disable iff and an explicit disable iff
defined inside the property apply act “asynchronously”.
Namely, they take precedence over and are not related to
the property’s clocking expression. See LRM for
sync_accept_on and sync_reject_on


Builtin Functions
==================



.. note::
    Several useful and common functions related to assertions
    are predefined. Search IEEE 1800-2012 for “sampled value
    functions” and “system functions”. The system functions
    return an instantaneous value. The sampled value functions
    describe behaviour over a number of cycles. “Cycle” is
    defined by the properties clock definition and not, for
    example, nS, pS, timescale or system hardware clock.


.. confval:: Syntax

    ``$past(expr, N)``;

    Returns the value ofexpr N cycles ago. N defaults to 1 if omitted.

    ``$rose(expr)``;

    Returns TRUE if expr is TRUE in this cycle and was FALSE in the previous cycle, otherwise returns FALSE.

    ``$fell(expr)``;

    Returns TRUE is expr is FALSE in this cycle and was TRUE in the previous cycle, otherwise returns FALSE.

    ``$stable(expr)``;

    Returns TRUE is expr has the same value this cycle as it did in the previous cycle, otherwise returns FALSE.

    ``$onehot(expr)``;

    Returns TRUE if expr has exactly one bit with the value 1’b1, otherwise returns FALSE.

    ``$onehot0(expr)``;

    Returns TRUE if expr has at most one bit with the value 1’b1, otherwise returns FALSE.

    ``$isunknown(expr)``;

    Returns TRUE if any bit of expr is 1’bX or 1’bZ , otherwise returns FALSE. Search JasperGold® command reference for
    *-enable_sva_isunknown*

    ``$countones(expr)``;

    Returns an integer which is the number of bits of expr which have the value 1’b1.


Example
-------

.. code:: python

      P13: assert property(req&&!gnt |=> $stable(addr));
      P14 : assert property ( $onehot(GNT_VEC)) );
      P15 : assert property ( ACCEPT_RX | -> $countones(ID_TAGS) != 10 );
      P15A: assert property(!RDY |=> DAT == $past(DAT) );



Different Dealys
==================

.. note::
    SVA properties cannot be unclocked. The clock must come
    from: an explicit clock declaration when the property is
    declared, an explicit clock declaration when the property is
    instantiated or a default clocking declaration.
    Explicit declaration will always override the default
    clocking. Sequences with no explicit clock declaration
    inherit the clock from their parent property. default
    clocking applies only to the current scope, in which it is
    defined.. Only one default clocking allowed per
    scope. Only P15_INS_B and P18 use the default clock.





.. confval:: Syntax

    ``default clocking`` MYCLK @(posedge clk2);
    ``endclocking`

Example
-------

.. code:: python

      property P15;
        A |=> B;
      endproperty
      property P16;
        @(posedge clk6) A |=> B;
      endproperty

      P16_I_A: assert property (@(posedge clk8) (P15) );
      P16_INS_B: assert property ( P15 );
      P17_INST: assert property ( P16 );
      P18: assert property ( @(posedge clk5) A | -> B );
      P19: assert property ( C | -> D );


If the entire design uses only posedge clk then it’s more
efficient ifposedge clk is used in *all* properties.

Updates will be release soon
============================
