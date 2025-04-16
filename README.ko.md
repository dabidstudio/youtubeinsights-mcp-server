# YouTube Insights MCP Server
[![PyPI version](https://badge.fury.io/py/youtubeinsights-mcp-server.svg)](https://pypi.org/project/youtubeinsights-mcp-server/)

YouTube 동영상에서 인사이트를 추출할 수 있는 Model Context Protocol (MCP) 서버입니다. 자막 파싱, 키워드 기반 동영상 검색, 채널 정보 조회 등의 기능을 제공합니다.

## 주요 기능

- YouTube 동영상의 자막 추출 (다국어 지원)
- 키워드 기반 동영상 검색 및 메타데이터 조회 (조회수, 좋아요, 썸네일 등)
- YouTube 동영상 URL을 통한 채널 정보 및 최신 동영상 조회
- FastMCP 기반 서버 통합으로 쉬운 배포
- MCP 도구를 통한 원활한 에이전트 워크플로우

## 설치 방법

### uvx 사용 (권장)

[`uvx`](https://docs.astral.sh/uv/guides/tools/)를 사용하는 경우 별도의 설치가 필요하지 않습니다.

MCP 설정 파일(예: Claude Desktop의 경우 `claude_desktop_config.json`)에 다음 설정을 추가하세요:

```json
{
  "mcpServers": {
    "youtubeinsights": {
      "command": "uvx",
      "args": ["youtubeinsights-mcp-server"],
      "env": {
        "YOUTUBE_API_KEY": "your-api-key",
      }
    }
  }
}
```

### 개발 환경 설치

1. 저장소 클론

   ```
2. `.env.example` 파일을 `.env`로 복사하고 YouTube Data API 인증 정보 입력

    ```json
    {
      "mcpServers": {
        "youtubeinsights": {
          "command": "uv",
          "args": [
            "--directory",
            "path/to/youtubeinsights-mcp-server",
            "run",
            "youtubeinsights-mcp-server"
          ],
          "env": {
            "YOUTUBE_API_KEY": "your-api-key",
          }
        }
      }
    }
    ```

## 사용 가능한 MCP 도구

- `get_youtube_transcript`: YouTube 동영상 URL에서 전체 자막 추출 (`ko`, `en` 지원)
- `search_youtube_videos`: 키워드로 YouTube 동영상 검색 및 주요 메타데이터 조회
- `get_channel_info`: YouTube 동영상 URL을 기반으로 채널 메타데이터 및 최신 업로드 동영상 조회

## MCP 도구 설명 예시

```json
{
  "tool": "get_youtube_transcript",
  "description": "주어진 YouTube 동영상 URL에서 자막을 추출합니다."
}
```

```json
{
  "tool": "search_youtube_videos",
  "description": "키워드로 동영상을 검색하고 조회수, 좋아요, 썸네일 등의 메타데이터를 반환합니다."
}
```

```json
{
  "tool": "get_channel_info",
  "description": "동영상 URL을 기반으로 채널 정보(제목, 구독자 수, 최신 업로드)를 조회합니다."
}
```

## 라이선스

이 프로젝트는 MIT 라이선스로 제공됩니다. 자세한 내용은 [LICENSE](LICENSE) 파일을 참조하세요. 
