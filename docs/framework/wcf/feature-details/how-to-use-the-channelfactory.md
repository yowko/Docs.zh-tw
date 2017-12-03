---
title: "HOW TO：使用 ChannelFactory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 37ad5181ad140c3ef3ea8ba5b3774fd44310dca7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-use-the-channelfactory"></a>HOW TO：使用 ChannelFactory
會在需要建立通道處理站的進階案例中使用泛型 <xref:System.ServiceModel.ChannelFactory%601> 類別，以建立多個通道。  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>建立及使用 ChannelFactory 類別  
  
1.  建置及執行 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][設計和實作服務](../../../../docs/framework/wcf/designing-and-implementing-services.md)，[設定服務](../../../../docs/framework/wcf/configuring-services.md)，和[裝載服務](../../../../docs/framework/wcf/hosting-services.md)。  
  
2.  使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來產生用戶端的合約 （介面）。  
  
3.  在用戶端程式碼中，使用 <xref:System.ServiceModel.ChannelFactory%601> 類別以建立多個端點接聽項。  
  
## <a name="example"></a>範例  
 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
