---
title: "WIF 組態結構描述慣例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
caps.latest.revision: 3
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 3
---
# WIF 組態結構描述慣例
本主題討論慣例使用在 Windows 識別基礎 \(WIF\) 設定主題中會說明用來 [\<system.identityModel\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) 和 [\<system.identityModel.services\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) 部分和屬性常用的一些功能。  
  
<a name="BKMK_Modes"></a>   
## 模式  
 許多 WIF 組態項目有 `mode` 屬性。  類別是用來進行處理的特定部分，而組態項目提供在目前項目的子項目的這個屬性通常是控制項。  設定將會引發錯誤。由於模式設定為，則為，如果在組態檔中的項目會被忽略。  
  
<a name="BKMK_TimespanValues"></a>   
## TimeSpan 值  
 其中是使用 <xref:System.TimeSpan> ，當屬性的型別，請參閱 <xref:System.TimeSpan.Parse%28System.String%29> 方法允許的格式。  這符合下列格式規格。  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 例如， 「30 "， 「30.00:00」， 「30.00:00: 00 "表示所有 30 天;而「00:05」， 「00:05: 00 "， 「0.00:05: 00.00 "表示所有 5 分鐘。  
  
<a name="BKMK_CertificateReferences"></a>   
## 憑證參考  
 巡覽至數個項目當做參考使用 `<certificateReference>` 項目。  當參考憑證時，下列屬性取得。  
  
|||  
|-|-|  
|`storeLocation`|<xref:System.Security.Cryptography.X509Certificates.StoreLocation> 列舉型別的值: `CurrentUser` 或 `CurrentMachine`。|  
|`storeName`|<xref:System.Security.Cryptography.X509Certificates.StoreName> 列舉型別的值，最適合這個內容是 `My` 和 `TrustedPeople`。|  
|`x509FindType`|<xref:System.Security.Cryptography.X509Certificates.X509FindType> 列舉型別的值，最適合這個內容是 `FindBySubjectName` 和 `FindByThumbprint`。  為了避免錯誤的機會，建議 `FindByThumbprint` 型別用於實際執行環境。|  
|`findValue`|使用的值是根據 `x509FindType` 屬性找到憑證。  為了避免錯誤的機會，建議 `FindByThumbprint` 型別用於實際執行環境。  當 `FindByThumbPrint` 指定時，這個屬性接受憑證指模的十六進位字串格式的值;例如， 「97249e1a5fa6bee5e515b82111ef524a4c91583f」。|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## 自訂型別參考  
 使用 `type` 屬性的幾個項目參考自訂型別。  這個屬性應該指定這個自訂型別的名稱。  若要參考從全域組件快取 \(GAC\) 的型別，應該使用強式名稱。  若要參考來自組件的型別 Bin 目錄中，簡單的組件限定參考可用於。  在 App\_Code\/資料庫目錄中所定義的型別可以藉由指定型別也參考名稱不限制的組件。  
  
 必須從這個型別衍生自訂型別指定，而且必須提供 `public` 預設 \(0 引數\) 建構函式。  
  
## 請參閱  
 [\<system.identityModel\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)   
 [\<system.identityModel.services\>](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)