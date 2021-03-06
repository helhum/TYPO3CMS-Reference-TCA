cropVariants
~~~~~~~~~~~~

:aspect:`Datatype`
    array

:aspect:`Scope`
    Proc. / Display

:aspect:`Description`
    Main crop, focus area and cover area configuration.

    Default configuration:

    .. code-block:: php

        'cropVariants' => [
            'default' => [
                'title' => 'LLL:EXT:lang/Resources/Private/Language/locallang_wizards.xlf:imwizard.crop_variant.default',
                'allowedAspectRatios' => [
                    '16:9' => [
                        'title' => 'LLL:EXT:lang/Resources/Private/Language/locallang_wizards.xlf:imwizard.ratio.16_9',
                        'value' => 16 / 9
                    ],
                    '3:2' => [
                        'title' => 'LLL:EXT:lang/Resources/Private/Language/locallang_wizards.xlf:imwizard.ratio.3_2',
                        'value' => 3 / 2
                    ],
                    '4:3' => [
                        'title' => 'LLL:EXT:lang/Resources/Private/Language/locallang_wizards.xlf:imwizard.ratio.4_3',
                        'value' => 4 / 3
                    ],
                    '1:1' => [
                        'title' => 'LLL:EXT:lang/Resources/Private/Language/locallang_wizards.xlf:imwizard.ratio.1_1',
                        'value' => 1.0
                    ],
                    'NaN' => [
                        'title' => 'LLL:EXT:lang/Resources/Private/Language/locallang_wizards.xlf:imwizard.ratio.free',
                        'value' => 0.0
                    ],
                ],
                'selectedRatio' => 'NaN',
                'cropArea' => [
                    'x' => 0.0,
                    'y' => 0.0,
                    'width' => 1.0,
                    'height' => 1.0,
                ],
            ],
        ]

    Above configuration is a fall back if no other more specific configuration has been given.

    It is possible to define multiple crop variants. The array key is used as identifier for the ratio and the label
    is specified with the "title" and the actual (floating point) ratio with the "value" key. The value **must** be of
    PHP type float, not only a string.

    .. code-block:: php

        'config' => [
            'type' => 'imageManipulation',
            'cropVariants' => [
                'mobile' => [
                    'title' => 'LLL:EXT:ext_key/Resources/Private/Language/locallang.xlf:imageManipulation.mobile',
                    'allowedAspectRatios' => [
                        '4:3' => [
                            'title' => 'LLL:EXT:lang/Resources/Private/Language/locallang_wizards.xlf:imwizard.ratio.4_3',
                            'value' => 4 / 3
                        ],
                        'NaN' => [
                            'title' => 'LLL:EXT:lang/Resources/Private/Language/locallang_wizards.xlf:imwizard.ratio.free',
                            'value' => 0.0
                        ],
                    ],
                ],
                'desktop' => [
                    'title' => 'LLL:EXT:ext_key/Resources/Private/Language/locallang.xlf:imageManipulation.desktop',
                    'allowedAspectRatios' => [
                        '4:3' => [
                            'title' => 'LLL:EXT:lang/Resources/Private/Language/locallang_wizards.xlf:imwizard.ratio.4_3',
                            'value' => 4 / 3
                        ],
                        'NaN' => [
                            'title' => 'LLL:EXT:lang/Resources/Private/Language/locallang_wizards.xlf:imwizard.ratio.free',
                            'value' => 0.0
                        ],
                    ],
                ],
            ]
        ]

    It is also possible to define an initial crop area. If no initial crop area is defined, the default selected
    crop area will cover the complete image. Crop areas are defined relatively with floating point numbers. The x and y
    coordinates and width and height must be specified for that. The below example has an initial crop area in the size
    the previous image cropper provided by default.

    .. code-block:: php

        'config' => [
            'type' => 'imageManipulation',
            'cropVariants' => [
                'mobile' => [
                    'title' => 'LLL:EXT:ext_key/Resources/Private/Language/locallang.xlf:imageManipulation.mobile',
                    'cropArea' => [
                        'x' => 0.1,
                        'y' => 0.1,
                        'width' => 0.8,
                        'height' => 0.8,
                    ],
                ],
            ],
        ]

    Users can also select a focus area, when configured. The focus area is always **inside** the crop area and mark the
    area in the image which must be visible for the image to transport its meaning. The selected area is persisted to
    the database but will have no effect on image processing. The data points are however made available as data
    attribute when using the `<f:image />` view helper.

    The below example adds a focus area, which is initially one third of the size of the image and centered.

    .. code-block:: php

        'config' => [
            'type' => 'imageManipulation',
            'cropVariants' => [
                'mobile' => [
                    'title' => 'LLL:EXT:ext_key/Resources/Private/Language/locallang.xlf:imageManipulation.mobile',
                    'focusArea' => [
                        'x' => 1 / 3,
                        'y' => 1 / 3,
                        'width' => 1 / 3,
                        'height' => 1 / 3,
                    ],
                ],
            ],
        ]

    Very often images are used in a context, where there are overlaid with other DOM elements like a headline. To give
    editors a hint which area of the image is affected, when selecting a crop area, it is possible to define multiple
    so called cover areas. These areas are shown inside the crop area. The focus area cannot intersect with any of
    the cover areas.

    .. code-block:: php

        'config' => [
            'type' => 'imageManipulation',
            'coverAreas' => [
                [
                    'x' => 0.05,
                    'y' => 0.85,
                    'width' => 0.9,
                    'height' => 0.1,
                ],
            ],
        ],
