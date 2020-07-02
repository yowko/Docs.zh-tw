---
ms.openlocfilehash: 3e8601ba76dfb05e3d70b3af7440bd7e228768d0
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621065"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>允許在與 UNC 共用相似的 URI 中使用 Unicode

#### <a name="details"></a>詳細資料

在 <xref:System.Uri?displayProperty=fullName> 中，若您建構的檔案 URI 同時包含 UNC 共用名稱和 Unicode 字元時，不會再導致 URI 出現無效的內部狀態。 這項行為只有在下列所有條件都符合時才會變更：<ul><li>URI 具有 <code>file:</code> 配置，且後接 4 條以上的斜線。</li><li>主機名稱開頭為底線或其他非保留符號。</li><li>URI 包含 Unicode 字元。</li></ul>

#### <a name="suggestion"></a>建議

如果應用程式使用的 URI 始終包含 Unicode，可想而知，該應用程式會使用這項行為來禁止參考 UNC 共用。 因此，這類應用程式應該改用 <xref:System.Uri.IsUnc>。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.7.2|
|類型|執行階段

#### <a name="affected-apis"></a>受影響的 API

-<xref:System.Uri?displayProperty=nameWithType></li></ul>|
