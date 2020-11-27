---
title: 作法：使用 ChannelFactory
description: 瞭解如何建立通道處理站，以建立多個通道以使用 WCF 用戶端來存取服務。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: dd767443fefb16ebc02300bffa4264357f12c3ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280581"
---
# <a name="how-to-use-the-channelfactory"></a>作法：使用 ChannelFactory

會在需要建立通道處理站的進階案例中使用泛型 <xref:System.ServiceModel.ChannelFactory%601> 類別，以建立多個通道。  
  
### <a name="to-create-and-use-the-channelfactory-class"></a>建立及使用 ChannelFactory 類別  
  
1. 建立並執行 Windows Communication Foundation (WCF) 服務。 如需詳細資訊，請參閱 [設計和執行服務](../designing-and-implementing-services.md)、設定 [服務](../configuring-services.md)和 [裝載服務](../hosting-services.md)。  
  
2. 使用 [ [System.servicemodel 中繼資料公用程式] 工具 ( # A0) ](../servicemodel-metadata-utility-tool-svcutil-exe.md) ，為用戶端產生合約 (介面) 。  
  
3. 在用戶端程式碼中，使用 <xref:System.ServiceModel.ChannelFactory%601> 類別以建立多個端點接聽項。  
  
## <a name="example"></a>範例  

 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
