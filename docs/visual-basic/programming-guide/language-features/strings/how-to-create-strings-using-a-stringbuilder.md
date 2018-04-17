---
title: 如何：在 Visual Basic 中使用 StringBuilder 建立字串
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0e15c7df07822ee104a88525c209768c05470e3
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>如何：在 Visual Basic 中使用 StringBuilder 建立字串
這個範例會建構從許多較小的字串使用長字串<xref:System.Text.StringBuilder>類別。 <xref:System.Text.StringBuilder>類別是更有效率`&=`運算子來串連多個字串。  
  
## <a name="example"></a>範例  
 下列範例會建立的執行個體<xref:System.Text.StringBuilder>類別，將 1000 的字串附加至該執行個體，，，然後傳回其字串表示。  
  
 [!code-vb[VbVbalrStrings#70](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-strings-using-a-stringbuilder_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [使用 StringBuilder 類別](../../../../standard/base-types/stringbuilder.md)  
 [&= 運算子](../../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [字串](../../../../visual-basic/programming-guide/language-features/strings/index.md)  
 [建立新字串](../../../../standard/base-types/creating-new.md)  
 [操作字串](../../../../standard/base-types/manipulating-strings.md)  
 [字串的範例](https://msdn.microsoft.com/library/be9e82a3-dc95-4aaa-9396-61b66e467e02(v=vs.100))
