---
ms.openlocfilehash: dfa8235fcfd868b80d3a610bddb492899519e289
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009045"
---
### <a name="xml-parsing-changes"></a>XML 剖析變更

| 名稱    | 值   |
|:--------|:--------|
| 範圍   | Minor   |
| 版本 | 4.5.2   |
| 類型    | 執行階段 |

#### <a name="details"></a>詳細資料

基於安全性考慮，下列變更已引入 XML 剖析 API：

- <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=nameWithType> 當初始化時，會設定為 10000000 <xref:System.Xml.XmlReaderSettings> 。
- 根據預設，<xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=nameWithType> 是設為 `null`。

> [!NOTE]
> <xref:System.Xml.XmlReaderSettings> 所有 XML 剖析器都會使用，因此雖然這項變更有助於這 <xref:System.Xml.XmlReader> 種情況，但它也會影響其他案例。

#### <a name="suggestion"></a>建議

若要還原為先前的行為，您可以在登錄中設定值。 將名為的 DWORD 值新增至登錄機 `EnableLegacyXmlSettings` `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework\XML` 碼，並將其值設定為 `1` 。 您也可以改為在 HKEY_CURRENT_USER hive 中新增登錄值。

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.Xml.XmlReaderSettings.MaxCharactersFromEntities?displayProperty=fullName>
- <xref:System.Xml.XmlReaderSettings.XmlResolver?displayProperty=fullName>

此外，任何相依于 <xref:System.Xml.XmlResolver> （直接或間接）的 XML API 都會受到影響。

<!--

#### Affected APIs

- `P:System.Xml.XmlReaderSettings.MaxCharactersFromEntities`
- `P:System.Xml.XmlReaderSettings.XmlResolver`

-->
