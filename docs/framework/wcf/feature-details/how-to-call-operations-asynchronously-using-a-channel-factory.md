---
title: HOW TO：使用通道處理站以非同步方式呼叫作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
ms.openlocfilehash: 0662b82661e4fb3cde85930c2c4544f541d3a2a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202725"
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a>HOW TO：使用通道處理站以非同步方式呼叫作業
本主題涵蓋用戶端如何能夠在使用 <xref:System.ServiceModel.ChannelFactory%601> 架構的用戶端應用程式時，非同步地存取服務作業  (當使用 <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> 物件來叫用服務時，您可以使用事件驅動的非同步呼叫模型。 如需詳細資訊，請參閱[如何：以非同步方式呼叫服務作業](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)。 如需事件架構非同步呼叫模型的詳細資訊，請參閱[事件架構非同步模式 (EAP)](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)。)  
  
 本主題中的服務會實作 `ICalculator` 介面。 用戶端可透過非同步的方式來呼叫在此介面上的作業，這表示類似 `Add` 的作業會分割為兩個方法，`BeginAdd` 和 `EndAdd`，其中前者會啟始呼叫，後者則會在作業完成時擷取結果。 如需示範如何在服務中以非同步方式實作作業的範例，請參閱[How to:實作非同步服務作業](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)。 如需同步與非同步作業的詳細資訊，請參閱[同步和非同步作業](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>若要以非同步方式呼叫 WCF 服務作業  
  
1.  執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具搭配`/async`選項，如下列命令所示。  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     這會針對作業的服務合約產生非同步用戶端版本。  
  
2.  建立要在非同步作業完成時呼叫的回呼函式 (Callback Function)，如下列範例程式碼所示。  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  若要以非同步方式來存取服務作業，請建立用戶端和呼叫 `Begin[Operation]` (例如，`BeginAdd`)，並指定回呼函式，如下列範例程式碼所示。  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     當此回呼函式執行時，用戶端便會呼叫 `End<operation>` (例如，`EndAdd`) 以擷取結果。  
  
## <a name="example"></a>範例  
 在用於上述程序中之用戶端程式碼所使用的服務會實作 `ICalculator` 介面，如下列程式碼所示。 在服務端，`Add`和`Subtract`合約作業的同時叫用由 Windows Communication Foundation (WCF) 執行階段，即使在用戶端上的 「 先前的用戶端步驟會叫用非同步。 在服務端，會使用 `Multiply` 和 `Divide` 作業來非同步叫用服務，即使用戶端會同步叫用這些服務也是一樣。 這個範例會將 <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> 屬性設定為 `true`。 這項屬性設定在配合 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 非同步模式 (Asynchronous Pattern) 的實作時，便會告知執行階段以非同步方式來叫用作業。  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
