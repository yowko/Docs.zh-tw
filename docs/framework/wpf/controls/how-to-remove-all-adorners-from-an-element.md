---
title: HOW TO：從元素移除所有 Adorner
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adorners [WPF], removing
ms.assetid: fe5303a3-b76e-4643-aafb-51419032b47b
ms.openlocfilehash: 8504bb1ec70de188033b2b092bbb66cf9da3dc11
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59116790"
---
# <a name="how-to-remove-all-adorners-from-an-element"></a>HOW TO：從元素移除所有 Adorner
此範例示範如何以程式設計方式移除所有裝飾指定<xref:System.Windows.UIElement>。  
  
## <a name="example"></a>範例  
 此詳細的程式碼範例會移除所有裝飾項中所傳回的裝飾項的陣列<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>。  此範例會擷取上的裝飾項<xref:System.Windows.UIElement>名為*myTextBox*。  呼叫中指定的項目<xref:System.Windows.Documents.AdornerLayer.GetAdorners%2A>有任何裝飾項，`null`會傳回。  此程式碼明確檢查有 null 的陣列，最適合應用程式的 null 陣列應該在其中應該相當常見。  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornerslong)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersLong](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornerslong)]  
  
## <a name="example"></a>範例  
 此壓縮之程式碼範例是功能上相當於上面顯示的詳細資訊的範例。 此程式碼不會明確檢查 null 的陣列，所以有可能，<xref:System.NullReferenceException>可能會引發例外狀況。  此程式碼最適合用於應用程式，使用 null 陣列應該很少見。  
  
 [!code-csharp[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/csharp/VS_Snippets_Wpf/AdornersMiscCode/CSharp/Window1.xaml.cs#_removealladornersshort)]
 [!code-vb[AdornersMiscCode#_RemoveAllAdornersShort](~/samples/snippets/visualbasic/VS_Snippets_Wpf/AdornersMiscCode/visualbasic/window1.xaml.vb#_removealladornersshort)]  
  
## <a name="see-also"></a>另請參閱

- [裝飾項概觀](adorners-overview.md)
