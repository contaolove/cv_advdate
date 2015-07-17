# Advanced date field
Provides the advanced date field widget for frontend and backend, which allows you to split up a 'date' field into 3 text or select fields for day, month and year.

# Dependencies
If you are not using Composer to install this widget, you will also need:
https://github.com/terminal42/contao-NamespaceClassLoader

# Languages
The widget is translated in
 * Englisch
 * German

# Installation and usage
Install it via Composer or just copy all files into system/modules/cv_advdate

DCA-Field example for use with text input fields
```
'myDateOfBirth_text' => array
(
    'label'                 => &$GLOBALS['TL_LANG']['tl_table']['myDateOfBirth_text'],
    'exclude'               => true,
    'inputType'             => 'cvAdvDate',
    'eval'                  => array
    (
        'mandatory'         => true,
        'widgetType'        => 'text',
        'ageCheck'          => 18
    ),
    'sql'                   => "varchar(11) NOT NULL default ''"
)
```
DCA-Field example for use with select fields
```
'myDateOfBirth_select' => array
(
    'label'                 => &$GLOBALS['TL_LANG']['tl_table']['myDateOfBirth_select'],
    'exclude'               => true,
    'inputType'             => 'cvAdvDate',
    'eval'                  => array
    (
        'mandatory'         => true,
        'widgetType'        => 'select',
        'monthNames'        => true,
        'dayOrder'          => 'desc',
        'monthOrder'        => 'desc',
        'yearOrder'         => 'desc',
        'ageCheck'          => 18,
        'rangeYear'         => array(1950, date('Y')),
        'limitYearToAge'    => true
    ),
    'sql'                   => "varchar(11) NOT NULL default ''"
)
```

Supported parameters for eval array

| Parameter | Default | For widgetType | Description |
| ------------- | ------------- | ------------- | ------------- |
| mandatory  | false | select, text | Contao default parameter |
| widgetType  | 'select' | - | Generates the widget either with input text fields or with select fields |
| monthNames  | false | select | Displays the select field for the month either with digits or with full month names |
| dayOrder  | 'asc' | select | Orders the digits of the select field for the day ascending or descending |
| monthOrder  | 'asc' | select | Orders the digits of the select field for the month ascending or descending |
| yearOrder  | 'asc' | select | Orders the digits of the select field for the year ascending or descending |
| ageCheck  | 0 | select, text | Calculates the age for the given value and prevent from saving if value is not valid |
| rangeYear  | 1900,date('Y') | select | The from-to range for the select field for the year field. If 'from' value is bigger then the 'to' value, the 'to' value minus 1 is taken |
| limitYearToAge  | false | select | The 'to' value of the year range will be limited to the age (e.g. ageCheck=18: date('Y') - 18 |
