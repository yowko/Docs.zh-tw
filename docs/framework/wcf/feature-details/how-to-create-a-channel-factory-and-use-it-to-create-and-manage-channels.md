---
title: HOW TO：建立通道處理站，並使用它來建立與管理通道
ms.date: 03/30/2017
ms.assetid: 018dcc30-9f61-419e-af8e-412a85e8d282
ms.openlocfilehash: 37ba8db3084f8d90aab33a08f6b52ddaee4545f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649527"
---
# <a name="how-to-create-a-channel-factory-and-use-it-to-create-and-manage-channels"></a>HOW TO：建立通道處理站，並使用它來建立與管理通道
針對可供用戶端用來傳送與接收在服務端點之間往返之訊息的不同雙工通道類型，<xref:System.ServiceModel.DuplexChannelFactory%601> 類別提供了這些雙工通道的建立與管理方式。  
  
## <a name="example"></a>範例  
 下列程式碼會顯示如何建立通道處理站，並使用它建立並管理通道。  
  
 [!code-csharp[S_CustomAuthentication#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_customauthentication/cs/instance.cs#1)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.ServiceModel.DuplexChannelFactory%601>
