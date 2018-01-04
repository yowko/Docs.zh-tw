---
title: "如何： 開啟訊息方塊"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1754fa190a638c1a200805e339f91bd582d27c4c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-message-box"></a>如何： 開啟訊息方塊
這個範例示範如何開啟訊息方塊。  
  
## <a name="example"></a>範例  
 訊息方塊是預先製作好強制回應對話方塊，可對使用者顯示資訊。 藉由呼叫靜態開啟訊息方塊<xref:System.Windows.MessageBox.Show%2A>方法<xref:System.Windows.MessageBox>類別。 當<xref:System.Windows.MessageBox.Show%2A>是呼叫，將訊息傳遞使用字串參數。 數個多載的<xref:System.Windows.MessageBox.Show%2A>讓您設定訊息方塊出現的方式 (請參閱<xref:System.Windows.MessageBox>)。  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>請參閱  
 [MessageBox 範例](http://go.microsoft.com/fwlink/?LinkID=160023)
