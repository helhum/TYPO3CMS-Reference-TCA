tableWizard
^^^^^^^^^^^

:aspect:`Datatype`
    array

:aspect:`Scope`
    fieldControl

:aspect:`Description`
    The table wizard field control is used in :code:`type='text'` with :code:`renderType='textTable'`
    elements and renders a button to the stand alone table wizard.

    The table wizard is used typically with the Content Elements, type "Table". It allows to edit
    the code-like configuration of the tables with a visual editor.

    Note the control button is only displayed after a new record has been saved the first time.

    .. figure:: ../../Images/TypeTextTableWizard1.png
        :alt: The table wizard

        The table wizard

    Available options:

    xmlOutput
      (boolean) If set to true, the output from the wizard is XML instead of the TypoScript table configuration code.
      Default false.

    numNewRows
      (integer) Setting the number of blank rows that will be added in the bottom of the table when the
      plus-icon is pressed. The default is 5, the range is 1-50.

    Example overriding defaults of a :code:`renderType='textTable'` element:

    .. code-block:: php

        'bodytext' => [
            'config' => [
                'fieldControl' => [
                    'options' => [
                        'numNewRows' => 3,
                    ],
                ],
            ],
        ],
