---
ms.openlocfilehash: 4d410811095786b33580d25f6c6eab3ac2f27148
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616036"
---
### <a name="resolveassemblyreference-task-now-warns-of-dependencies-with-the-wrong-architecture"></a>ResolveAssemblyReference 工作現在會發出警告，指出相依於錯誤的架構

#### <a name="details"></a>詳細資料

這項工作會發出警告 MSB3270，指出某個參考或參考的任何一個相依性不符合應用程式的架構。 例如，如果使用 `AnyCPU` 選項編譯的應用程式包含 x86 參考，則會發生此情況。 這類情況會導致應用程式在執行階段失敗 (在本範例中，如果應用程式部署為 x64 處理序)。

#### <a name="suggestion"></a>建議

影響可分為下列兩方面：

- 重新編譯會產生在舊版 MSBuild 下編譯應用程式時未顯示的警告。 不過，由於此警告識別執行階段失敗的可能來源，因此應該加以調查和解決。
- 如果將警告視為錯誤，應用程式將無法編譯。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Minor       |
| 版本 | 4.5.1       |
| 類型    | 正在重定目標 |
