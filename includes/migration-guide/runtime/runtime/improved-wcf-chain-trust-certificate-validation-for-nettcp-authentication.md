---
ms.openlocfilehash: e12ba8eb53e6725ebc2e1d87edff3a6a3ce2116b
ms.sourcegitcommit: 5d9f4b805787f890ca6e0dc7ea30a43018bc9cbb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2019
ms.locfileid: "58467475"
---
### <a name="improved-wcf-chain-trust-certificate-validation-for-nettcp-certificate-authentication"></a>針對 Net.Tcp 憑證驗證改善的 WCF 鏈結信任憑證驗證

|   |   |
|---|---|
|詳細資料|.NET Framework 4.7.2 若以傳輸安全性搭配 WCF 使用憑證驗證，就可以改善鏈結信任憑證驗證。 利用這項改善，必須針對用戶端驗證設定用來驗證伺服器的用戶端憑證。  同樣地，必須針對伺服器驗證設定用來驗證伺服器的伺服器憑證。 利用這項變更，如果已停用根憑證，憑證鏈結驗證就會失敗。 同時，已透過 Windows 安全性彙總對 .NET Framework 3.5 和更新版本進行了相同的變更。 您可以在[這裡](https://support.microsoft.com/en-us/help/4055269/security-only-update-for-net-framework-3-5-1-4-5-2-4-6-4-6-1-4-6-2-4-7)找到更多資訊。這項變更預設為開啟，而且可以透過組態設定加以關閉。|
|建議|<ul><li>驗證您的伺服器和用戶端憑證是否具有必要的 EKU OID。 如果沒有，請更新您的憑證。</li><li>驗證您的根憑證是否無效。 如果是，請更新根憑證。</li><li>如何選擇退出變更：如果無法更新憑證，您可以使用下列組態設定暫時解決這項重大變更；不過，選擇退出此變更會使您的系統容易受到安全性問題影響。</li></ul><pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;wcf:useLegacyCertificateUsagePolicy&quot; value=&quot;true&quot; /&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|範圍|次要|
|版本|4.7.2|
|類型|執行階段|

