---
title: HOW TO：使用 Windows Communication Foundation 服務 Moniker，但不註冊
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], service monikers without registration
ms.assetid: ee3cf5c0-24f0-4ae7-81da-73a60de4a1a8
ms.openlocfilehash: 3ce388da75711ab1378ce59575c067cf828089e8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54615268"
---
# <a name="how-to-use-the-windows-communication-foundation-service-moniker-without-registration"></a>HOW TO：使用 Windows Communication Foundation 服務 Moniker，但不註冊
若要連接到並與 Windows Communication Foundation (WCF) 服務進行通訊，WCF 用戶端應用程式必須有服務位址、 繫結組態和服務合約的詳細資料。  
  
 WCF 服務 moniker 通常取得必要的合約，透過之前註冊的必要的屬性型別，但可能會有，這並不可行的情況。 如果沒有註冊，Moniker 可使用 `wsdl` 參數、中繼資料交換和使用 `mexAddress` 參數，即可用 Web 服務定義語言 (WSDL) 文件格式來取得合約的定義。  
  
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
  
 若要建構下列範例 moniker 字串的遠端服務的 WCF 用戶端可以使用。  
  
```  
service4:mexAddress="http://servername/Affiliates/service.svc/mex",  
address="http://servername/Affiliates/service.svc",  
contract=IAffiliate, contractNamespace=http://Microsoft.ServiceModel.Demo,  
binding=WSHttpBinding_IAffiliate, bindingNamespace=http://tempuri.org/  
```  
  
 在執行用戶端應用程式期間，用戶端會使用提供的 `WS-MetadataExchange` 來執行 `mexAddress`。 這樣做可能會對一些服務傳回位址、繫結和合約詳細資訊。 您可以使用 `address`, `contract`, `contractNamespace`, `binding` 和 `bindingNamespace` 參數來識別要用的服務。 一旦這些參數都符合，moniker 建構適當的合約定義的 WCF 用戶端，並呼叫便可使用 WCF 用戶端中，如同具型別合約。  
  
> [!NOTE]
>  如果 Moniker 的格式錯誤或服務無法使用，則呼叫 `GetObject` 時將會傳回「無效的語法」錯誤。 如果您收到這個錯誤，請確定您所使用的 Moniker 正確無誤，而且此服務為可用狀態。  
  
## <a name="see-also"></a>另請參閱
- [如何：註冊並設定服務 Moniker](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)
