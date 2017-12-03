---
title: "實作服務合約"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 688637ae54e92296d103a681715dd491ba8782ba
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="implementing-service-contracts"></a>實作服務合約
服務是一種類別，會在一或多個端點公開可供用戶端使用的功能。 如果要建立服務，請寫入實作 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 合約的類別。 您可以使用下列其中一種作法： 您可以將合約另外定義為介面，然後建立實作該介面的類別。 或者，您可以將 <xref:System.ServiceModel.ServiceContractAttribute> 屬性置於類別本身，而將 <xref:System.ServiceModel.OperationContractAttribute> 屬性置於可供服務之用戶端使用的方法上，以直接建立類別和合約。  
  
## <a name="creating-a-service-class"></a>建立服務類別  
 以下是實作已另外定義之 `IMath` 合約的服務範例。  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 或者，服務可以直接公開合約。 以下是定義及實作 `MathService` 合約的服務類別範例。  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 請注意，前述服務會公開不同的合約，因為合約名稱不同。 在第一個案例中，公開的合約名為 "`IMath`"，而在第二個案例中，合約名為 "`MathService`"。  
  
 您可以在服務和作業實作層級進行一些設定，例如並行和執行個體。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][設計和實作服務](../../../docs/framework/wcf/designing-and-implementing-services.md)。  
  
 在實作服務合約之後，必須為服務建立一或多個端點。 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][端點建立概觀](../../../docs/framework/wcf/endpoint-creation-overview.md)。 [!INCLUDE[crabout](../../../includes/crabout-md.md)]執行服務，請參閱[裝載服務](../../../docs/framework/wcf/hosting-services.md)。  
  
## <a name="see-also"></a>另請參閱  
 [設計與實作服務](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [如何： 使用合約類別，建立服務](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)  
 [如何： 建立服務合約介面](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)  
 [指定服務執行階段行為](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
