---
ms.openlocfilehash: af10716fe5f4c07091e8605cdf620e4a499fb1e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619941"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>IPad 不應用於自訂功能檔案，因為現在它是一種瀏覽器功能

#### <a name="details"></a>詳細資料

從 .NET Framework 4.5 開始，iPad 是預設 ASP.NET 瀏覽器功能檔案中的識別碼，所以不應將其用於自訂功能檔案

#### <a name="suggestion"></a>建議

如果需要 iPad 特定功能，則必須以修改 iPad 行為，方法是在預先定義的閘道 refID &quot;IPad&quot; 上設定功能　，而不是透過使用者代理程式比對產生新的 &quot;IPad&quot; 識別碼。

| 名稱    | 值       |
|:--------|:------------|
| 影響範圍   |Edge|
|版本|4.5|
|類型|執行階段|
