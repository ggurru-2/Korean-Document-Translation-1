# AI-NFT의 메타데이터

AI-NFT 생성은 기존의 NFT 생성 과정과 유사하지만, **`ai_agent` 필드**가 추가됩니다. 이 필드는 AI 에이전트의 설정 및 사용 엔진을 의미하며, 해당 정보는 메타데이터에 저장됩니다.

## 지원되는 AI 엔진 <a href="#metadata-json" id="metadata-json"></a>

<table><thead><tr><th width="224">엔진</th><th width="231">엔진 이름</th><th>캐릭터 파일</th></tr></thead><tbody><tr><td><a href="https://github.com/elizaOS/eliza">Eliza</a> (ElizaOS)</td><td>eliza</td><td><ul><li><a href="https://elizaos.github.io/eliza/docs/core/characterfile/">사용 설명서</a></li><li><a href="https://github.com/elizaOS/characterfile">템플릿</a></li><li><a href="https://github.com/elizaOS/eliza/tree/main/characters">예제</a></li></ul></td></tr></tbody></table>

## AI-NFT 메타데이터 JSON <a href="#metadata-json" id="metadata-json"></a>

| 필드                          | 유형    | 설명                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| ---------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **ai\_agent** (새로 추가됨)  | object | <p>이 NFT에 연결된 AI 에이전트의 설정</p><ul><li><strong>engine</strong> (string): AI 에이전트를 실행하는 데 사용되는 엔진. 기본값은 "eliza"</li><li><strong>character</strong> (object): AI 에이전트를 설명하는 JSON 형식의 캐릭터 파일. 자세한 내용은 <a href="https://github.com/elizaOS/characterfile?tab=readme-ov-file">여기</a>를 참조하세요.</li></ul>                                                                                                                                                                                     |
| **name**                     | string | 자산의 이름                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| **description**              | string | 자산의 설명                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **image**                    | string | 자산의 로고를 의미하는 URI                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 |
| **animation\_url**           | string | 자산의 애니메이션을 의미하는 URI                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| **external\_url**            | string | 자산을 설명하는 외부 URL을 의미하는 URI — 예를 들어 게임의 공식 웹사이트                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| **attributes**               | array  | <p>자산의 특성을 정의하는 속성 배열</p><ul><li><strong>trait_type</strong> (string): 속성 유형</li><li><strong>value</strong> (string): 속성 값</li></ul>                                                                                                                                                                                                                                                                                                                                        |
| **properties**               | object | <p>자산의 특성을 정의하는 추가 속성</p><ul><li><p><strong>files</strong> (array): 자산과 함께 포함되는 추가 파일</p><ul><li><strong>uri</strong> (string): 파일의 URI</li><li><strong>type</strong> (string): 파일 유형, 예: <code>image/png</code>, <code>video/mp4</code></li><li><strong>cdn</strong> (boolean, optional): 파일이 CDN에서 제공되는지 여부</li></ul></li><li><strong>category</strong> (string): 자산의 미디어 카테고리, 예: <code>video</code>, <code>image</code></li></ul> |

## 예시

```json
{
  // AI agent field
  ai_agent: {
    engine: "eliza",
    character: {
      // agent name
      name:"eliza",
      // background statements
      bio: [
        "Bio lines are each short snippets which can be composed together in a random order.",
        "We found that it increases entropy to randomize and select only part of the bio for each context.",
        "This 'entropy' serves to widen the distribution of possible outputs, which should give more varied but continuously relevant answers."
      ],
      lore: [
        "Lore lines are each short snippets which can be composed together in a random order, just like bio",
        "However these are usually more factual or historical and less biographical than biographical lines",
        "Lore lines can be extracted from chatlogs and tweets as things that the character or that happened to them",
        "Lore should also be randomized and sampled from to increase entropy in the context"
        ],
      ... //xxx.character.json from https://github.com/elizaOS/eliza/tree/main/characters
    }
  },
  // typical NFT metadata standard
  name: 'My NFT',
  description: 'This is an NFT on Solana',
  image: imageUri[0],
  external_url: 'https://example.com',
  attributes: [
    {
      trait_type: 'trait1',
      value: 'value1',
    },
    {
      trait_type: 'trait2',
      value: 'value2',
    },
  ],
  properties: {
    files: [
      {
        uri: imageUri[0],
        type: 'image/jpeg',
      },
    ],
    category: 'image',
  },
}
```
