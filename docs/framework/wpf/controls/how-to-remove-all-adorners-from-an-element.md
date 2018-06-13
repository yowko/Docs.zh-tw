---
title: 如何：移除項目的所有裝飾項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
ms.openlocfilehash: 5b7e2038c8a314a180ba097a30c124f874c25893
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551612"
---
# <a name="how-to-remove-all-adorners-from-an-element"></a>如何：移除項目的所有裝飾項
這個範例示範如何以程式設計方式移除所有裝飾指定<xref:System.Windows.UIElement>。  
  
## <a name="example"></a>範例  
 這個冗長的程式碼範例會移除所有裝飾項的提示所傳回陣列中<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>。  此範例中會發生要擷取的裝飾項在<xref:System.Windows.UIElement>名為*myTextBox*。  如果指定的呼叫中的項目<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>有無裝飾項，`null`傳回。  此程式碼明確檢查 null 的陣列，以及最適合應用程式其中 null 陣列必須是相對常見。  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a>範例  
 此壓縮的程式碼範例是功能上相當於上面顯示的詳細資訊的範例。 此程式碼不會明確地檢查 null 的陣列，所以有可能，<xref:System.NullReferenceException>可能會引發例外狀況。  此程式碼最適合用於應用程式的 null 陣列應該很少見。  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a>另請參閱  
 [裝飾項概觀](../../../../docs/framework/wpf/controls/adorners-overview.md)
