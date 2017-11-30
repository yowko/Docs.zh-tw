---
title: "整合 COM 應用程式概觀"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4e995fc66a925cb0ebe272c9dceca1ba63b9459d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="integrating-with-com-applications-overview"></a>整合 COM 應用程式概觀
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 為 Managed 程式碼開發人員提供了一個資源豐富的作業環境，讓他們可以建立相關應用程式。 不過，如果您對 Unmanaged COM 架構程式碼做了大筆投資，而且不想進行移轉，則仍舊可以使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 Moniker 將 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web 服務直接移轉至現有的程式碼。 服務 Moniker 可以從多種 COM 架構開發環境中使用，例如 Office VBA、Visual Basic 6.0 或 Visual C++ 6.0。  
  
> [!NOTE]
>  服務 Moniker 會在所有的通訊中使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 通訊通道。 該通道的安全性和識別機制不同於標準 COM 和 DCOM Proxy 所使用的機制。 此外，服務 Moniker 會使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 通訊通道，所以任何呼叫的預設逾時期間都是一分鐘。  
  
 服務 Moniker 會搭配 `GetObject` 函式使用，提供 Unmanaged 開發人員強型別且專屬於 COM 的方法來呼叫 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web 服務。 這個動作需要有 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web 服務合約的本機 COM 可見定義，以及要使用的繫結。 正如其他 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端一樣，雖然在第一次呼叫方法時，COM 程式設計人員看得見這個通道建構過程，但服務 Moniker 仍必須建構服務的型別通道。  
  
 與其他 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端共通的是，當使用 Moniker 時，應用程式會將位址、繫結及合約指定為與服務通訊。 可以使用下列其中一種方法指定合約：  
  
-   型別合約：合約會在用戶端電腦上註冊為 COM 可見型別。  
  
-   WSDL 合約：合約會以 WSDL 文件的形式提供。  
  
-   MEX 合約：合約會在執行階段從中繼資料交換 (MEX) 端點擷取。  
  
## <a name="parameters-supported-by-the-service-moniker"></a>服務 Moniker 支援的參數  
 下表顯示服務 Moniker 所支援的參數。  
  
|參數|說明|  
|---------------|-----------------|  
|`address`|服務的 URL 位置。|  
|`binding`|應用程式組態中的繫結區段名稱。|  
|`bindingConfiguration`|具名繫結區段中的具名繫結執行個體。|  
|`contract`|介面識別項 (IID)，表示服務合約或合約名稱 (來自 MEX)。|  
|`wsdl`|WSDL 文件，提供其他形式的合約定義。|  
|`spnIdentity`|伺服器主要名稱 (SPN) 身分識別，用於與服務進行通訊。|  
|`upnIdentity`|使用者主要名稱 (UPN) 身分識別，用於與服務進行通訊。|  
|`dnsIdentity`|DNS 身分識別，用於與服務進行通訊。|  
|`mexAddress`|服務中繼資料交換 (MEX) 端點的 URL 位置。|  
|`mexBinding`|要連接 MEX 端點之應用程式組態中的繫結區段名稱。|  
|`mexBindingConfiguration`|要連接 MEX 端點之具名繫結區段中的具名繫結執行個體。|  
|`bindingNamespace`|在擷取的 MEX 中，繫結區段名稱的命名空間。|  
|`contractNamespace`|在擷取的 MEX 中，合約的命名空間。|  
|`mexSpnIdentity`|伺服器主要名稱 (SPN) 身分識別，用於與 MEX 端點進行通訊。|  
|`mexUpnIdentity`|使用者主要名稱 (UPN) 身分識別，用於與 MEX 端點進行通訊。|  
|`mexDnsIdentity`|DNS 身分識別，用於與 MEX 端點進行通訊。|  
|`serializer`|指定要使用 "xml" 或 "datacontract" 序列化程式。|  
  
> [!NOTE]
>  即使搭配整個 COM 架構用戶端使用，服務 Moniker 仍需要用戶端電腦上安裝 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 和支援的 .NET Framework 2.0。 此外，使用服務 Moniker 的用戶端應用程式也一定要載入適當版本的 .NET Framework 執行階段。 在 Office 應用程式中使用 Moniker 時，可能需要有組態檔來確認是否載入了正確的 Framework 版本。 例如，在 Excel 中應將下列文字放入與 Excel.exe 檔案位在相同的目錄下，而且名為 Excel.exe.config 的檔案中：  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  `<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a>另請參閱  
 [如何： 註冊並設定服務 Moniker](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
