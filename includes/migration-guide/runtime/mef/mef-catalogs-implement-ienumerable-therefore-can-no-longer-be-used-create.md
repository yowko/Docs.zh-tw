---
ms.openlocfilehash: 598df2121b480d411dac9c5571772a4a8d22b5ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620036"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5 開始，MEF 目錄會實作 IEnumerable，因此不能再用來建立序列化程式 (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> 物件)。 嘗試序列化 MEF 目錄會擲回例外狀況。

#### <a name="suggestion"></a>建議

無法再使用 MEF 建立序列化程式

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |主要|
|版本|4.5|
|類型|執行階段|
