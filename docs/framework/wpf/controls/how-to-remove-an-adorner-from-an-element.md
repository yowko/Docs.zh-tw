---
title: 如何：從項目移除裝飾項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: a3e1b08a9ec5e2cd60c063ced5e5f0d5874f8184
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-remove-an-adorner-from-an-element"></a>如何：從項目移除裝飾項
這個範例示範如何以程式設計方式移除特定的裝飾項指定<xref:System.Windows.UIElement>。  
  
## <a name="example"></a>範例  
 這個冗長的程式碼範例的提示所傳回陣列中移除第一個裝飾項<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>。  此範例中會發生要擷取的裝飾項在<xref:System.Windows.UIElement>名為*myTextBox*。  如果指定的呼叫中的項目<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>有無裝飾項，`null`傳回。  此程式碼明確檢查 null 的陣列，以及最適合應用程式其中 null 陣列必須是相對常見。  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a>範例  
 此壓縮的程式碼範例是功能上相當於上面顯示的詳細資訊的範例。 此程式碼不會明確地檢查 null 的陣列，所以有可能，<xref:System.NullReferenceException>可能會引發例外狀況。  此程式碼最適合用於應用程式的 null 陣列應該很少見。  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a>另請參閱  
 [裝飾項概觀](../../../../docs/framework/wpf/controls/adorners-overview.md)
