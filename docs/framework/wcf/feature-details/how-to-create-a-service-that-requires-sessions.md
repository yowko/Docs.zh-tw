---
title: "HOW TO：建立需要工作階段的服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a7613ef-0df9-47c3-b8dc-47f42cb1fd8b
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# HOW TO：建立需要工作階段的服務
工作階段會在兩個或更多的端點之間建立共用狀態，以啟用諸如回呼、多重躍點安全性之類的有用功能，並在用戶端與服務執行個體之間建立關聯。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]中的工作階段[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]應用程式，請參閱[使用工作階段的](../../../../docs/framework/wcf/using-sessions.md)。  
  
### <a name="to-specify-that-a-contract-require-its-binding-to-support-sessions"></a>指定合約需要自身繫結來支援工作階段  
  
1.  建立其中至少包含一個作業的服務合約。 如需如何建立服務合約的範例，請參閱[How to︰ 定義服務合約](../../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)。  
  
2.  修改<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=fullName>藉由設定宣告合約<xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=fullName>屬性設為︰  
  
    -   <xref:System.ServiceModel.SessionMode?displayProperty=fullName>如果必須在工作階段內執行合約。  
  
    -   <xref:System.ServiceModel.SessionMode?displayProperty=fullName>如果可以在工作階段內執行合約。  
  
    -   <xref:System.ServiceModel.SessionMode?displayProperty=fullName>如果不得在工作階段中執行這個合約。  
  
3.  將您的服務端點設定為使用支援工作階段的繫結。 下列組態範例示範使用<xref:System.ServiceModel.WSDualHttpBinding?displayProperty=fullName>，可支援 WS`-`ReliableMessaging 工作階段。  
  
     [!code[SCA.Session#2](../../../../samples/snippets/common/VS_Snippets_CFX/sca.session/common/hostapplication.exe.config#2)]
     [!code-csharp[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
     [!code-vb[SCA.Session#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/hostapplication.exe.config#2)]  
  
## <a name="example"></a>範例  
 下列程式碼範例示範如何指定合約層級的工作階段需求，並使用組態檔來支援該需求<xref:System.ServiceModel.WSDualHttpBinding?displayProperty=fullName>繫結。  
  
 [!code-csharp[SCA.Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/services.cs#1)]
 [!code-vb[SCA.Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/services.vb#1)]  
  
 [!code[SCA.Session#2](../../../../samples/snippets/common/VS_Snippets_CFX/sca.session/common/hostapplication.exe.config#2)]
 [!code-csharp[SCA.Session#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/sca.session/cs/hostapplication.exe.config#2)]
 [!code-vb[SCA.Session#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.session/vb/hostapplication.exe.config#2)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=fullName>   
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=fullName>   
 <xref:System.ServiceModel.SessionMode?displayProperty=fullName>