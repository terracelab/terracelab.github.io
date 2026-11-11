# 설치

## 지금 (0.x 미리보기)

npm에 아직 공개하지 않았습니다. 그때까지는 두 가지 방법으로 씁니다.

**모노레포 안**: `workspace:*`로 의존합니다.

```json
{
  "dependencies": {
    "@terracelab/trellis-tokens": "workspace:*",
    "@terracelab/trellis-react": "workspace:*"
  }
}
```

**다른 저장소**: Trellis 저장소에서 패키지를 tgz로 묶어 설치합니다.

```bash
# Trellis 저장소에서
pnpm build
pnpm --filter @terracelab/trellis-tokens pack --pack-destination ../tgz
pnpm --filter @terracelab/trellis-contracts pack --pack-destination ../tgz
pnpm --filter @terracelab/trellis-react pack --pack-destination ../tgz

# 내 앱에서
pnpm add ../tgz/terracelab-trellis-tokens-0.0.0.tgz ../tgz/terracelab-trellis-contracts-0.0.0.tgz ../tgz/terracelab-trellis-react-0.0.0.tgz
```

## npm에 공개되면

공개 npm에서 바로 설치합니다. `.npmrc`나 토큰은 필요 없습니다.

```bash
pnpm add @terracelab/trellis-tokens @terracelab/trellis-react
```

## 요구 사항

- React 19, react-dom 19(peer). 차트는 Recharts 3을 내장 의존성으로 가져옵니다.
- 번들러: Vite · Next.js · Astro 등 ESM을 이해하는 도구. 패키지는 ESM만 냅니다.
- 모든 `@terracelab/trellis-*`는 **같은 버전**을 설치합니다. 섞으면 토큰과 컴포넌트가 어긋납니다.

## 확인

```ts
import { formatAmount } from '@terracelab/trellis-contracts';
formatAmount(1234567, { unit: '원' }); // "1,234,567원"
```

다음: [CSS · 테마 · 밀도](setup.md)
