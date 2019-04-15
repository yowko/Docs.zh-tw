---
ms.openlocfilehash: e39b4e85b47902babac7a22a93aa64c2f86ef01f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236722"
---
### <a name="dataobjectgetdata-now-retrieves-data-as-utf-8"></a>DataObject.GetData 現在會以 UTF-8 形式來擷取資料

|   |   |
|---|---|
|詳細資料|若為以 .NET Framework 4.5.1 為目標的應用程式，或者在 .NET Framework 4.5.1 或舊版上執行的應用程式，<code>DataObject.GetData</code> 會以 ASCII 字串形式來擷取 HTML 格式的資料。 因此，非 ASCII 字元 (ASCII 碼大於 0x7F 的字元) 會以兩個隨機字元表示。<p/>若為以 .NET Framework 4.5 或更新版本為目標並且在 .NET Framework 4.5.2 上執行的應用程式，<code>DataObject.GetData</code> 會以 UTF-8 形式來擷取 HTML 格式的資料，以正確地表示大於 0x7F 的字元。|
|建議|如果針對 HTML 格式字串的編碼問題實作了因應措施 (例如將從 [剪貼簿] 擷取的 HTML 字串傳遞至 <xref:System.Text.UTF8Encoding.GetString(System.Byte[],System.Int32,System.Int32)?displayProperty=name> 以明確將其編碼)，並將目標從應用程式 4 版重定為 4.5 版，則應該移除該因應措施。如果因故需要舊版行為，應用程式可以將目標設為 .NET Framework 4.0 來取得該行為。|
|範圍|Edge|
|版本|4.5.2|
|類型|正在重定目標|
|受影響的 API|<ul><li><xref:System.Windows.DataObject.GetData(System.String)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.Type)?displayProperty=nameWithType></li><li><xref:System.Windows.DataObject.GetData(System.String,System.Boolean)?displayProperty=nameWithType></li></ul>|
