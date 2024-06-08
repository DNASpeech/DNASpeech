## DNASpeech: DNASpeech: A Contextualized and Situated Text-to-Speech Dataset with Dialogues, Narratives and Actions

DNASpeech is a novel text-to-speech dataset with high-quality speeches with **DNA** prompt annotations (**D**ialogue context, **N**arratives and **A**ction states). DNASpeech contains 2,395 distinct characters, 4,4529 scenes, and 22,975 dialogue utterances, along with over 18 hours of high-quality10 speech recordings, which provides text-to-speech task with more detailed description.

## Usage
### Installation
You can download DNASpeech dataset through this [link](https://drive.google.com/drive/folders/14DAmOQhIuqyR9kduJr1iRLqXljV00BLc?usp=drive_link), which contains three files: **DNASpeech_meta.json, DNASpeech_wav.zip and DNASpeech_raw.zip.**

|       **FILE**      | **SIZE** |                 **DESCRIPTION**                 |
|:-------------------:|:--------:|:------------------------------------------------|
| DNASpeech_meta.json |   584MB  | Contains the meta data of speeches in DNASpeech |
| DNASpeech_wav.zip   |   2.9GB  | Denoised speech data                            |
| DNASpeech_raw.zip   |   6.9GB  | Original speech data                            |

### Metadata File
**DNASpeech_meta.json** is in JSON line format and contains 22,975 lines. Each line represents a sample from DNASpeech, with the following fields:

|     **FIELD**    |  **TYPE**  |                                                              **DESCRIPTION**                                                              |
|:----------------:|:----------:|:------------------------------------------------------------------------------------------------------------------------------------------|
| **index**        | **String** | unique key for a sample in the format 'SpeakerID-MovieID-LineID', which also serves as the file name of corresponding speech clip (.wav). |
| **scene**        |  **Dict**  | contains 2 sub-fields                                                                                                                     |
|            scene |   String   | scene title                                                                                                                               |
|            lines |    List    | full content of a scene that extracted from the movie script                                                                              |
| **character**    | **String** | speaker name                                                                                                                              |
| **timestamp**    |  **Tuple** | start and end timestamp of the corresponding speech clip in the movie, formatted as HH:MM:SS,MS                                           |
| **narrative**    |  **List**  | environment description of the speech                                                                                                     |
| **dialogue**     |  **List**  | dialogue context of the speech                                                                                                            |
| **action_state** | **String** | action, expression or some extra information of the speaker                                                                               |
| **text**         | **String** | content text of the corresponding speech                                                                                                  |
| **ASR_text**     | **String** | transcribed text obtained using ASR technology corresponding to the speech clip.                                                          |
| **score**        |   **Int**  | manual assessment of data quality from 1 to 3.                                                                                            |

Below is a detailed example. For more examples, please refer to DNASpeech_meta.json.

```json
{
    "index": '1431-101-117',
    "scene": {
        "scene": "268 INT -- MESS HALL -- DAY (1966) 268",
        "lines": [
            {
                "type": "description",
                "content": "Heywood is regaling the table with some anecdote about Andy."
            },
            {
                "type": "dialogue",
                "character": "RED",
                "content": "Those of us who knew him best talk about him often. I swear, the stuff he pulled. It always makes us laugh.",
                "extra": "V.O."
            },
            {
                "type": "description",
                "content": "A wild burst of laughter. PUSH IN on Red. Feeling melancholy."
            },
            {
                "type": "dialogue",
                "character": "RED",
                "content": "Sometimes it makes me sad, though, Andy being gone. I have to remind myself that some birds aren't meant to be caged, that's all. Their feathers are just too bright...",
                "extra": "V.O."
            }
        ]
    },
    "character": "RED",
    "timestamp": [
        "02:05:00,076",
        "02:05:02,954"
    ],
    "dialogue": [],
    "narrative": [
        "Heywood is regaling the table with some anecdote about Andy."
    ],
    "action_state": "V.O.",
    "text": "Those of us who knew him best talk about him often.",
    "SAR_text": "Those of us who knew him best talk about him often.",
    "score": 3
}
```

### Audio File
**NDASpeech_wav** contains the denoised audio files corresponding to each sample in the dataset, with a total of 22,975 files, each file contains a speech clip. All files are in wav format with a sampling rate of 16K HZ. Each file is named according to the format: ‘SpeakerID-MovieID-LineID’, corresponding to the ‘index’ field in DNASpeech_meta. Specifically:

- **SpeakerID**: The ID of the speaker, ranging from 1 to 2395
- **MovieID**: The ID of the corresponding movie, ranging from 1 to 126
- **LineID**: The audio sequence number, ranging from 1 to the total number of speeches by the speaker

If you wish to obtain the original, unprocessed audio files, we provide **DNASpeech_raw**, which contains the same content as NDASpeech_wav, but with all audio files in their raw, unprocessed state.

## License
All data is distributed under the CC BY-NC-SA 4.0 license. 

Given the sensitive nature of biometric data, particularly vocal recordings, all data undergo anonymization to protect personal privacy. However, despite these measures, there exists a potential risk of misuse. **To prevent unauthorized usage or dissemination, access to the dataset is subject to a rigorous review process.** Regarding the intended use, users are permitted to define their own tasks in our dataset under the license, upon advanced contact with [us](chengchuanqi@ruc.edu.cn).
