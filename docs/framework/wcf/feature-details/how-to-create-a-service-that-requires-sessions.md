---
title: HOW TO：建立需要工作階段的服務
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
ms.openlocfilehash: 495de5a926cfc0c5aab88337f5f33b991c49e71a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184995"
---
# <a name="how-to-create-a-service-that-requires-sessions"></a>HOW TO：建立需要工作階段的服務
工作階段會在兩個或更多的端點之間建立共用狀態，以啟用諸如回呼、多重躍點安全性之類的有用功能，並在用戶端與服務執行個體之間建立關聯。 有關 Windows 通信基礎 （WCF） 應用程式中的會話的詳細資訊，請參閱[使用會話](../../../../docs/framework/wcf/using-sessions.md)。  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>指定合約需要自身繫結來支援工作階段  
  
1. 建立其中至少包含一個作業的服務合約。 有關如何創建服務協定的示例，請參閱[如何：定義服務協定](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)。  
  
2. 將 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType> 屬性設為下列其中一項，以修改宣告合約的 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>：  
  
    - <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType> (如果必須在工作階段內執行合約的話)。  
  
    - <xref:System.ServiceModel.SessionMode.Allowed?displayProperty=nameWithType> (如果可以在工作階段內執行合約的話)。  
  
    - <xref:System.ServiceModel.SessionMode.NotAllowed?displayProperty=nameWithType> (如果不得在工作階段內執行合約的話)。  
  
3. 將您的服務端點設定為使用支援工作階段的繫結。 下列組態範例說明可支援 WS<xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>ReliableMessaging 工作階段的 `-` 用法。  
  
     [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="example"></a>範例  
 下列程式碼範例說明如何指定合約層級的工作階段需求，以及透過組態檔並使用 <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> 繫結程序來支援該需求。  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]
 [!code-xml[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType>
- <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType>
