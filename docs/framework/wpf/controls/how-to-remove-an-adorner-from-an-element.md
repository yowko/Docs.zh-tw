---
title: HOW TO：從項目移除裝飾項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: 97cf4d9f-0596-429e-8526-32a30aa4ae99
ms.openlocfilehash: eeefa83703ef9a4ffa7653042745d9acd58536f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54695750"
---
# <a name="how-to-remove-an-adorner-from-an-element"></a>HOW TO：從項目移除裝飾項
此範例示範如何以程式設計方式從指定中移除特定的裝飾項<xref:System.Windows.UIElement>。  
  
## <a name="example"></a>範例  
 此詳細的程式碼範例所傳回的裝飾項的陣列中移除第一個裝飾項<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>。  此範例會擷取上的裝飾項<xref:System.Windows.UIElement>名為*myTextBox*。  呼叫中指定的項目<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>有任何裝飾項，`null`會傳回。  此程式碼明確檢查有 null 的陣列，最適合應用程式的 null 陣列應該在其中應該相當常見。  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornerlong)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerLong](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornerlong)]  
  
## <a name="example"></a>範例  
 此壓縮之程式碼範例是功能上相當於上面顯示的詳細資訊的範例。 此程式碼不會明確檢查 null 的陣列，所以有可能，<xref:System.NullReferenceException>可能會引發例外狀況。  此程式碼最適合用於應用程式，使用 null 陣列應該很少見。  
  
 [!code-csharp[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removespecificadornershort)]
 [!code-vb[AdornersMiscCode#_RemoveSpecificAdornerShort](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removespecificadornershort)]  
  
## <a name="see-also"></a>另請參閱
- [裝飾項概觀](../../../../docs/framework/wpf/controls/adorners-overview.md)
