---
ms.openlocfilehash: 424e8ff704b888aa3d2c1254ac712da4034f59b8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85616038"
---
### <a name="obsoleteattribute-exports-as-both-obsoleteattribute-and-deprecatedattribute-in-winmd-scenarios"></a>ObsoleteAttribute 會在 WinMD 案例中匯出為 ObsoleteAttribute 和 DeprecatedAttribute

#### <a name="details"></a>詳細資料

當您建立 Windows 中繼資料庫 (.winmd 檔案) 時，<xref:System.ObsoleteAttribute?displayProperty=fullName> 屬性會匯出為 <xref:System.ObsoleteAttribute?displayProperty=fullName> 和 [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute)。

#### <a name="suggestion"></a>建議

重新編譯使用 <xref:System.ObsoleteAttribute?displayProperty=fullName> 屬性的現有來源程式碼，可能會在從 C++/CX 或 JavaScript 使用該程式碼時產生警告。我們不建議您在受控組件中同時套用 <xref:System.ObsoleteAttribute?displayProperty=fullName> 和 [Windows.Foundation.DeprecatedAttribute](https://docs.microsoft.com/uwp/api/windows.foundation.metadata.deprecatedattribute)，這樣可能會導致建置警告。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   | Edge        |
| 版本 | 4.5.1       |
| 類型    | 正在重定目標 |
