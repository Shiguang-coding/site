---
title: Variables
---

{% youtube T9oAax-IRw0 %}

### 전역 변수

| 변수       | 설명                                  | Type                                    |
| -------- | ----------------------------------- | --------------------------------------- |
| `site`   | 사이트 전체의 정보.                         | `object`; see [Site Variables][]        |
| `page`   | 페이지 정보와 front-matter의 사용자 정의 변수 집합. | `object`; see [Page Variables][]        |
| `config` | 사이트 환경설정                            | `object` (your site's \_config file)  |
| `theme`  | 테마 환경설정. 사이트 환경설정을 상속합니다.           | `object` (your theme's \_config file) |
| `path`   | 현재 페이지의 경로                          | `string`                                |
| `url`    | 현재 페이지의 전체 경로                       | `string`                                |
| `env`    | 환경설정 변수                             | ???                                     |

{% note warn %}
Lodash has been removed from global variables since Hexo 5.0.0. [You-Dont-Need-Lodash-Underscore](https://github.com/you-dont-need/You-Dont-Need-Lodash-Underscore) might be helpful for your migration.
{% endnote %}

### 사이트 변수

| 변수                | 설명      | Type                   |
| ----------------- | ------- | ---------------------- |
| `site.posts`      | 모든 포스트  | [Query][queryo] object |
| `site.pages`      | 모든 페이지  | [Query][queryo] object |
| `site.categories` | 모든 카테고리 | [Query][queryo] object |
| `site.tags`       | 모든 태그   | [Query][queryo] object |

### 페이지 변수

**Article (page)**

| 변수                 | 설명                                                          | Type                                     |
| ------------------ | ----------------------------------------------------------- | ---------------------------------------- |
| `page.title`       | 게시글 제목                                                      | `string`                                 |
| `page.date`        | Article created date                                        | 게시글 생성 날짜 ([Moment.js][] object)         |
| `page.updated`     | Article last updated date                                   | 게시글이 마지막으로 갱신된 날짜 ([Moment.js][] object) |
| `page.comments`    | 코멘트를 활성화 할지 여부                                              | `boolean`                                |
| `page.layout`      | 레이아웃명                                                       | `string`                                 |
| `page.content`     | 게시글에서 full 처리될 컨텐츠                                          | `string`                                 |
| `page.excerpt`     | 게시글 발췌                                                      | `string`                                 |
| `page.more`        | 게시글 발췌를 제외한 컨텐츠                                             | `string`                                 |
| `page.source`      | 소스 파일의 경로                                                   | `string`                                 |
| `page.full_source` | 소스 파일의 전체 경로                                                | `string`                                 |
| `page.path`        | 루트 URL을 제외한 게시글의 URL. 테마에서는 `url_for(page.path)`를 자주 사용합니다. | `string`                                 |
| `page.permalink`   | 게시글의 전체 URL                                                 | `string`                                 |
| `page.prev`        | 이전 포스트, 현재 포스트가 첫 포스트라면 `null`입니다.                          | ???                                      |
| `page.next`        | 다음 포스트, 현재 포스트가 마지막 포스트라면 `null`입니다.                        | ???                                      |
| `page.raw`         | 게시글의 raw 데이터                                                | ???                                      |
| `page.photos`      | 게시글의 사진들 (Gallery post를 사용한 것들)                             | array of ???                             |
| `page.link`        | 게시글의 외부 링크 (Link post를 사용한 것들)                              | `string`                                 |

**Post (post):** `page` 레이아웃과 동일하지만 아래의 변수를 추가로 갖습니다.

| 변수                | 설명                               | Type           |
| ----------------- | -------------------------------- | -------------- |
| `page.published`  | Post가 draft상태가 아니라면 true를 반환합니다. | `boolean`      |
| `page.categories` | Post의 모든 카테고리                    | `array` of ??? |
| `page.tags`       | Post의 모든 태그                      | `array` of ??? |

**Home (index)**

| 변수                 | 설명                                                             | Type     |
| ------------------ | -------------------------------------------------------------- | -------- |
| `page.per_page`    | 한 페이지에 보여질 포스트의 수                                              | `number` |
| `page.total`       | 페이지의 전체 개수                                                     | `number` |
| `page.current`     | 현재 페이지의 번호                                                     | `number` |
| `page.current_url` | 현재 페이지의 URL                                                    | `string` |
| `page.posts`       | 이 페이지에 있는 포스트들 ([Data Model])                                  | `object` |
| `page.prev`        | 이전 페이지 번호. 현재 페이지가 첫 페이지라면 `0`입니다.                             | `number` |
| `page.prev_link`   | 이전 페이지의 URL. 현재 페이지가 첫 페이지라면 `''`입니다.                          | `string` |
| `page.next`        | 다음 페이지 번호. 현재 페이지가 마지막 페이지라면 `0`입니다.                           | `number` |
| `page.next_link`   | 다음 페이지의 URL. 현재 페이지가 마지막 페이지라면 `''`입니다.                        | `string` |
| `page.path`        | 루트 URL을 제외한 현재 페이지의 URL. 테마에서는 `url_for(page.path)`를 자주 사용합니다. | `string` |

**Category (category):** `index` 레이아웃과 동일하지만 아래의 변수를 추가로 갖습니다.

| 변수             | 설명                     | Type      |
| -------------- | ---------------------- | --------- |
| `page.archive` | `true`와 동일합니다.         | `boolean` |
| `page.year`    | 아카이브 연도 (4자리 숫자)       | `number`  |
| `page.month`   | 아카이브 월 (0을 제외한 2자리 숫자) | `number`  |

**Tag (tag):** `index` 레이아웃과 동일하지만 아래의 변수를 추가로 갖습니다.

| 변수              | 설명    | Type     |
| --------------- | ----- | -------- |
| `page.category` | 카테고리명 | `string` |

**Archive (archive):** `index` 레이아웃과 동일하지만 아래의 변수를 추가로 갖습니다.

| 변수         | 설명  | Type     |
| ---------- | --- | -------- |
| `page.tag` | 태그명 | `string` |

[queryo]: https://hexojs.github.io/warehouse/classes/query.default.html

[Moment.js]: http://momentjs.com/
[Site Variables]: #Site-Variables
[Page Variables]: #Page-Variables
