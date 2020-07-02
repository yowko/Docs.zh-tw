---
title: 如何：建立簡單繫結
description: 透過 Windows Presentation Foundation （WPF）中的此作法範例，為您的應用程式建立簡單的系結。
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 63dc44b442bb4658382bf12faf57b51c8e0698bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618697"
---
# <a name="how-to-create-a-simple-binding"></a>如何：建立簡單繫結
這個範例會示範如何建立簡單的 <xref:System.Windows.Data.Binding> 。  
  
## <a name="example"></a>範例  
 在此範例中，您的 `Person` 物件具有名為的字串屬性 `PersonName` 。 `Person`物件是在名為的命名空間中定義 `SDKSample` 。  
  
 在下列範例中包含元素的反白顯示行會 `<src>` 具現化 `Person` 具有 `PersonName` 屬性值的物件 `Joe` 。 這會在區段中完成 `Resources` ，並指派 `x:Key` 。  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 包含元素的反白顯示行接著會將控制項系結 `<TextBlock>` <xref:System.Windows.Controls.TextBlock> 至 `PersonName` 屬性。 因此， <xref:System.Windows.Controls.TextBlock> 會顯示值為 "Joe" 的。  
  
## <a name="see-also"></a>另請參閱

- [資料系結總覽](../../../desktop-wpf/data/data-binding-overview.md)
- [操作說明主題](data-binding-how-to-topics.md)
