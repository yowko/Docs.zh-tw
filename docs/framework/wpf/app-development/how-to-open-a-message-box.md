---
title: HOW TO：開啟訊息方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: 1bde7c4f794ca7e3b01490db8e918b06b5074bcf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54739728"
---
# <a name="how-to-open-a-message-box"></a>HOW TO：開啟訊息方塊
此範例示範如何開啟訊息方塊。  
  
## <a name="example"></a>範例  
 訊息方塊是預先強制回應對話方塊向使用者顯示資訊。 開啟訊息方塊，藉由呼叫靜態<xref:System.Windows.MessageBox.Show%2A>方法的<xref:System.Windows.MessageBox>類別。 當<xref:System.Windows.MessageBox.Show%2A>是呼叫，將訊息傳遞使用字串參數。 數個多載<xref:System.Windows.MessageBox.Show%2A>可讓您將會出現訊息方塊的方式 (請參閱<xref:System.Windows.MessageBox>)。  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>另請參閱
- [MessageBox 範例](https://go.microsoft.com/fwlink/?LinkID=160023)
