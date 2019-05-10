---
title: 晚期繫結程序解析; 可能發生執行階段錯誤
ms.date: 07/20/2015
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
ms.openlocfilehash: 6b78dfed1d615ba865f136365eac1c9c131ed5a5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64661941"
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>晚期繫結程序解析; 可能發生執行階段錯誤
物件會指派給宣告為變數[Object Data Type](../../../visual-basic/language-reference/data-types/object-data-type.md)。  
  
 當您宣告一個變數`Object`，編譯器必須執行*晚期繫結*，這會導致額外的作業在執行階段。 它也可能會讓您的應用程式發生執行階段錯誤。 比方說，如果您指派<xref:System.Windows.Forms.Form>要`Object`變數，然後嘗試存取<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType>屬性，執行階段會擲回<xref:System.MemberAccessException>因為<xref:System.Windows.Forms.Form>類別並未公開`NameTable`屬性。  
  
 如果您宣告為特定類型的變數，編譯器可以執行*早期繫結*在編譯時期。 如此可改善效能、 控制存取權的特定型別、 成員和您的程式碼的可讀性。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42017  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
- 可能的話，將特定類型的變數宣告。  
  
## <a name="see-also"></a>另請參閱

- [早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [物件變數宣告](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
