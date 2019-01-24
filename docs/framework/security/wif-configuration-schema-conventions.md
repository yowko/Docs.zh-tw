---
title: WIF 組態結構描述慣例
ms.date: 03/30/2017
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
author: BrucePerlerMS
ms.openlocfilehash: acdce1f0ae35713dd4955e1353e0a83000898408
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54711391"
---
# <a name="wif-configuration-schema-conventions"></a>WIF 組態結構描述慣例
本主題討論 Windows Identity Foundation (WIF) 組態主題中所使用的慣例，並描述 [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) 和 [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) 區段中所使用的一些常見功能和屬性。  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a>模式  
 許多 WIF 組態元素都有 `mode` 屬性。 這個屬性通常會控制哪一個類別用來執行處理的特定部分，以及哪一個組態元素允許作為目前元素的子元素。 如果組態檔中包含的項目會因模式設定而被忽略，將會引發組態錯誤。  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a>TimeSpan 值  
 如果 <xref:System.TimeSpan> 作為屬性的類型，請檢閱 <xref:System.TimeSpan.Parse%28System.String%29> 方法以查看允許的格式。 此格式符合以下規格。  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 例如，"30"、"30.00:00"、"30.00:00:00" 全都表示 30 天；"00:05"、"00:05:00"、"0.00:05:00.00" 全都表示 5 分鐘。  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a>憑證參考  
 數個項目會使用 `<certificateReference>` 元素來參考憑證。 參考憑證後，便可使用下列屬性。  
  
|||  
|-|-|  
|`storeLocation`|<xref:System.Security.Cryptography.X509Certificates.StoreLocation> 列舉值：`CurrentUser` 或 `CurrentMachine`。|  
|`storeName`|<xref:System.Security.Cryptography.X509Certificates.StoreName> 列舉值；此內容最有用的是 `My` 和 `TrustedPeople`。|  
|`x509FindType`|<xref:System.Security.Cryptography.X509Certificates.X509FindType> 列舉值；此內容最有用的是 `FindBySubjectName` 和 `FindByThumbprint`。 若要消除發生錯誤的機率，建議在生產環境中使用 `FindByThumbprint` 類型。|  
|`findValue`|用來根據 `x509FindType` 屬性尋找憑證的值。 若要消除發生錯誤的機率，建議在生產環境中使用 `FindByThumbprint` 類型。 指定 `FindByThumbPrint` 後，這個屬性接受的值是憑證指紋的十六進位字串格式；例如，"97249e1a5fa6bee5e515b82111ef524a4c91583f"。|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a>自訂類型參考  
 數個項目使用 `type` 屬性參考自訂類型。 這個屬性應該指定自訂類型的名稱。 若要從全域組件快取 (GAC) 中參考類型，應該使用強式名稱。 若要從 Bin/ 目錄中的組件參考類型，可能會使用簡單的組件限定參考。 定義在 App_Code/ 目錄中的類型，也可透過簡單指定不含合格組件的類型名稱來參考。  
  
 自訂類型必須衍生自指定的類型，而且必須提供 `public` 預設 (0 個引數) 建構函式。  
  
## <a name="see-also"></a>另請參閱
- [\<system.identityModel>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)
- [\<system.identityModel.services>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
