---
title: 如何：開啟訊息方塊
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: bd2c4dce78e46163eb4628cb3aab829fc0173edf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123723"
---
# <a name="how-to-open-a-message-box"></a>如何：開啟訊息方塊
這個範例顯示如何開啟訊息方塊。  
  
## <a name="example"></a>範例  
 訊息方塊是用來向使用者顯示資訊的換成強制回應對話方塊。 藉由呼叫 <xref:System.Windows.MessageBox> 類別的靜態 <xref:System.Windows.MessageBox.Show%2A> 方法，即可開啟訊息方塊。 呼叫 <xref:System.Windows.MessageBox.Show%2A> 時，會使用字串參數來傳遞訊息。 <xref:System.Windows.MessageBox.Show%2A> 的數個多載可讓您設定訊息方塊的顯示方式（請參閱 <xref:System.Windows.MessageBox>）。  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>另請參閱

- [MessageBox 範例](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)
