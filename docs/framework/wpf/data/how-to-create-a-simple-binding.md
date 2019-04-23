---
title: HOW TO：建立簡單繫結
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: d617c8b97aa679398ed2d061a652f5164f1e499b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094381"
---
# <a name="how-to-create-a-simple-binding"></a>HOW TO：建立簡單繫結
此範例將示範如何建立簡單<xref:System.Windows.Data.Binding>。  
  
## <a name="example"></a>範例  
 在此範例中，您必須`Person`物件具有名為字串屬性`PersonName`。 `Person`物件定義在命名空間中`SDKSample`。  
  
 反白顯示包含的那一行`<src>`項目，在下列範例會具現化`Person`物件`PersonName`屬性值為`Joe`。 這在完成`Resources`區段，然後指派`x:Key`。  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 包含反白顯示的列`<TextBlock>`項目再將繫結<xref:System.Windows.Controls.TextBlock>若要控制`PersonName`屬性。 如此一來， <xref:System.Windows.Controls.TextBlock> "Joe"的值會出現。  
  
## <a name="see-also"></a>另請參閱

- [資料繫結概觀](data-binding-overview.md)
- [HOW-TO 主題](data-binding-how-to-topics.md)
