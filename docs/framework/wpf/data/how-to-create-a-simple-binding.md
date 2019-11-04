---
title: 如何：建立簡單繫結
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: faef59ed426059eb2d488d0584d3325c8d46d415
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453506"
---
# <a name="how-to-create-a-simple-binding"></a>如何：建立簡單繫結
這個範例會示範如何建立簡單的 <xref:System.Windows.Data.Binding>。  
  
## <a name="example"></a>範例  
 在此範例中，您有一個 `Person` 物件，其中具有名為 `PersonName`的字串屬性。 `Person` 物件是在名為 `SDKSample`的命名空間中定義。  
  
 在下列範例中包含 `<src>` 元素的反白顯示行，會以 `Joe`的 `PersonName` 屬性值來具現化 `Person` 物件。 這會在 `Resources` 區段中完成，並指派 `x:Key`。  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 包含 `<TextBlock>` 元素的反白顯示行，接著會將 <xref:System.Windows.Controls.TextBlock> 控制項系結至 `PersonName` 屬性。 因此，<xref:System.Windows.Controls.TextBlock> 會出現 "Joe" 值。  
  
## <a name="see-also"></a>請參閱

- [資料繫結概觀](../../../desktop-wpf/data/data-binding-overview.md)
- [「如何」主題](data-binding-how-to-topics.md)
