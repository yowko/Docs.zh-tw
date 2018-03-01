---
title: "HOW TO：使用 Windows Communication Foundation 服務 Moniker 且不註冊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 18f575e9bae37b66526d7b61a641374266ba627b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>HOW TO：使用 Windows Communication Foundation 服務 Moniker 且不註冊
若要連線至 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務並進行通訊，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端應用程式必須具備詳細的服務位址、繫結組態和服務合約。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務 Moniker 經常透過之前註冊的必要屬性型別來取得必要的合約，但也可能會有不適用的情形發生。 如果沒有註冊，Moniker 可使用 `wsdl` 參數、中繼資料交換和使用 `mexAddress` 參數，即可用 Web 服務定義語言 (WSDL) 文件格式來取得合約的定義。  
  
 所適用的案例包括散發 Excel 試算表，在試算表中有些儲存格的值會透過 Web 服務互動計算而來。 在此案例中，可能無法在開啟文件的所有用戶端上註冊服務合約組件。 `wsdl` 參數或 `mexAddress` 參數將會啟用獨立的 (Self-Contained) 解決方案。  
  
> [!NOTE]
>  您必須使用相互驗證以保護要求和回應不會被竄改或詐騙。 特別重要的是，用戶端必須確定發出回應的中繼資料交換端點為預期的信任的一方。  
  
## <a name="example"></a>範例  
 這個範例會顯示搭配使用服務 Moniker 和 MEX 合約。 將使用 wsHttpBinding 公開具有下列合約的服務。  
  
```  
using System.ServiceModel;  
  
...  
  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Demo")]  
public interface IAffiliate  
{  
    [OperationContract]  
    bool NewAffiliate(string ID, string company, string fullname, string accountsCode);  
    [OperationContract]  
    bool RemoveAffiliate(string ID);  
    [OperationContract]  
    double RevenueCheckMonthly(ref string ID);  
    [OperationContract]  
    double RevenueCheckTotal(ref string ID);  
}  
```  
  
 若要對遠端服務建構 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端，您可以使用下列範例 Moniker 字串。  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 在執行用戶端應用程式期間，用戶端會使用提供的 `WS-MetadataExchange` 來執行 `mexAddress`。 這樣做可能會對一些服務傳回位址、繫結和合約詳細資訊。 您可以使用 `address`, `contract`, `contractNamespace`, `binding` 和 `bindingNamespace` 參數來識別要用的服務。 這些參數都符合之後，Moniker 會使用適當的合約定義來建構 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端，接著便可使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端來產生呼叫，就如同使用具有型別的合約一樣。  
  
> [!NOTE]
>  如果 Moniker 的格式錯誤或服務無法使用，則呼叫 `GetObject` 時將會傳回「無效的語法」錯誤。 如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。  
  
## <a name="see-also"></a>請參閱  
 [如何：註冊和設定服務 Moniker](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
