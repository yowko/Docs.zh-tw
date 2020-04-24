---
title: 如何:使用字串產生器建立字串
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: c41db584df83782dab99b90043045aa2cabcb6ff
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645331"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>如何:在視覺化基礎使用字串產生器建立字串

此示例使用<xref:System.Text.StringBuilder>類從許多較小的字串構造長字串。 類<xref:System.Text.StringBuilder>`&=`比 運算串聯許多字串更有效。

## <a name="example"></a>範例

下面的範例建立類的<xref:System.Text.StringBuilder>實體,將 1,000 個字串附加到該實體,然後傳回其字串表示形式:

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>另請參閱

- [使用 StringBuilder 類別](../../../../standard/base-types/stringbuilder.md)
- [&= 運算子](../../../language-reference/operators/and-assignment-operator.md)
- [字串](index.md)
- [建立新字串](../../../../standard/base-types/creating-new.md)
- [操作字串](../../../../standard/base-types/best-practices-strings.md)
