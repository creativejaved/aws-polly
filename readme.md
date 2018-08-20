## AWS Polly Text-To-Speech PHP Library

Convert written text into natural-sounding audio in a variety of languages and voices.  
This package use [AWS Polly](https://aws.amazon.com/polly/) service.

---
### Using the Library

#### Installation

Intall library in PHP project using composer
```
composer require tbetool/aws-polly
```

#### Using Library

After installing the library, create `WatsonTts` object
```
$polly = new AwsPolly(
    'aws_key', 
    'aws_secret', 
    'aws_region'
);
```
AWS `key, secret` can be obtained by creating IAM user in AWS console. For more detail follow [Creating IAM for Polly](https://console.bluemix.net/docs/services/text-to-speech/getting-started.html#gettingStarted).

#### Setting output path
Set absolute path of the directory where to save the output. You don't need to provide a file name as it will be auto generated.
```
$path = '/aboslute/path/to/directory';

$polly->setOutputPath($path);
```

**NOTE:** You can also pass output path with textToVoice() which will override this path

#### Convert Text to Speech
Pass text to convert to speech.
```
$file = $polly->textToVoice(
    'Hello World',
    $param
);
```
**$params** should be array and can have following content.
```
$param = [
    'language' => 'en-US',
    'voice' => 'Justin',
    'output_path' => '/absolute/file/path'
]
```
This will return the absolute path of the file created if text to speech conversion is successful, otherwise will throw Exception.

---
### Exception handling

Every function throws an Exception in case of any error/issue. Bind the code block within `try-catch` block to catch any exception occurred.

_Ex:_
```
try {
    $polly->textToVoice('Hello world');
} catch (Exception $exception) {
    echo $exception->getMessage();
}
```

---
### Other callable methods

##### Get supported languages
```
$polly->getLanguages();
```

_default:_ `en-US`
##### Get supported voices
```
$polly->getVoices();
``` 
_default:_ `Ivy`

---
### Supported language and voice list
list of supported language and voice strings

Name | language | voice | gender | description
--- | --- | --- | --- | ---
es-LA_SofiaVoice | **es-LA** | **SofiaVoice** | female | Sofia: Latin American Spanish (español latinoamericano) female voice.
pt-BR_IsabelaVoice | **pt-BR** | **IsabelaVoice** | female | Isabela: Brazilian Portuguese (português brasileiro) female voice.
en-GB_KateVoice | **en-GB** | **KateVoice** | female | Kate: British English female voice.
de-DE_BirgitVoice | **de-DE** | **BirgitVoice** | female | Birgit: Standard German of Germany (Standarddeutsch) female voice.
en-US_AllisonVoice | **en-US** | **AllisonVoice** | female | Allison: American English female voice.
fr-FR_ReneeVoice | **fr-FR** | **ReneeVoice** | female | Renee: French (français) female voice.
it-IT_FrancescaVoice | **it-IT** | **FrancescaVoice** | female | Francesca: Italian (italiano) female voice.
es-ES_LauraVoice | **es-ES** | **LauraVoice** | female | Laura: Castilian Spanish (español castellano) female voice.
ja-JP_EmiVoice | **ja-JP** | **EmiVoice** | female | Emi: Japanese (日本語) female voice.
es-ES_EnriqueVoice | **es-ES** | **EnriqueVoice** | male | Enrique: Castilian Spanish (español castellano) male voice.
de-DE_DieterVoice | **de-DE** | **DieterVoice** | male | Dieter: Standard German of Germany (Standarddeutsch) male voice.
en-US_LisaVoice | **en-US** | **LisaVoice** | female | Lisa: American English female voice.
en-US_MichaelVoice | **en-US** | **MichaelVoice** | male | Michael: American English male voice.
es-US_SofiaVoice | **es-US** | **SofiaVoice** | female | Sofia: North American Spanish (español norteamericano) female voice.

---
### Bug Reporting

If you found any bug, create an [issue](https://github.com/TBETool/aws-polly/issues/new).

---
### Support and Contribution

Something is missing? 
* `Fork` the repositroy
* Make your contribution
* make a `pull request`

