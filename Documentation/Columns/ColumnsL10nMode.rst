l10n\_mode
----------

:aspect:`Datatype`
    string (keyword)

:aspect:`Scope`
    Display / Proc.

:aspect:`Description`
    Localization mode.

    Only active if the :ref:`['ctrl']['languageField'] <ctrl-reference-languagefield>` property is set.

    The main relevance is when a record is localized by an API call in DataHandler that makes a copy of the default
    language record. You can think of this process as copying all fields from the source record, except if a special
    mode applies as defined below:

    Keywords are:

    exclude
        Field will not be shown in FormEngine if this record is a localization of the default language. Works basically
        like a display condition. Internally, the field value of the default language record is copied over to the
        field of the localized record. The DataHandler keeps the values of localized records in sync and actively copies
        a changed value from the default language record into the localized overlays if changed.

    prefixLangTitle
        The field value from the default language record gets copied when an localization overlay is created, but the
        content is prefixed with the title of the target language. The field stays editable in the localized record.
        Works only for field types like "text" and "input".

        The example shows the "header" field of a "tt\_content" record after a translation from default language
        english with content "English header" to danish has been created.

        .. figure:: ../Images/ColumnsL10nModePrefixLangTitle.png
            :alt: "Header" field of a tt_content record after translation has been created

            "Header" field of a tt_content record after translation

    If this property is not set for a given field, the value of the default language record is copied over to the
    localized record on creation, the field value is then distinct from the default language record, can be edited
    at will and will never be overwritten by the DataHandler if the value of the default language record changes.
