﻿.. include:: ../../Includes.txt

.. _columns-radio:

type = 'radio'
--------------

.. _columns-radio-introduction:

Introduction
============

This type creates a set of radio buttons. The value is typically stored as integer value, each radio
item has one assigned number, but it can be a string, too.


.. _columns-radio-examples:

Examples
========

.. figure:: ../../Images/TypeRadioStyleguide1.png
    :alt: A set of radio buttons

    A set of radio buttons

.. code-block:: php

    'radio_1' => [
        'label' => 'radio_1 three options',
        'config' => [
            'type' => 'radio',
            'items' => [
                [ 'foo', 1 ], // 'foo' should be a LLL reference
                [ 'bar', 2 ],
                [ 'foobar', 3 ],
            ],
        ],
    ],


renderType default
==================

type='radio' has (currently) only one render definition, no special renderType must be set.

.. _columns-radio-properties:

.. _columns-radio-properties-type:

.. _columns-radio-properties-default:
.. include:: ../Properties/CommonDefault.rst

.. _columns-radio-properties-fieldInformation:
.. include:: ../Properties/CommonFieldInformation.rst

.. _columns-radio-properties-fieldWizard:
.. include:: ../Properties/CommonFieldWizard.rst
.. include:: ../FieldWizard/DefaultLanguageDifferences.rst
.. include:: ../FieldWizard/LocalizationStateSelector.rst
.. include:: ../FieldWizard/OtherLanguageContent.rst

.. _columns-radio-properties-items:
.. include:: ../Properties/RadioItems.rst

.. _columns-radio-properties-itemsprocfunc:
.. include:: ../Properties/CommonItemsProcFunc.rst

.. _columns-radio-properties-readOnly:
.. include:: ../Properties/CommonReadOnly.rst
