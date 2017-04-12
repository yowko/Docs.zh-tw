---
title: "晚期繫結的解析;可能發生執行階段錯誤 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
dev_langs:
- VB
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3ac885b0de2c4f44d4323487fc55cde9b23defa4
ms.lasthandoff: 03/13/2017

---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>晚期繫結程序解析; 可能發生執行階段錯誤
在物件指派給變數宣告為[Object 資料型別](../../../visual-basic/language-reference/data-types/object-data-type.md)。  
  
 當您將變數宣告為`Object`，編譯器必須執行*晚期繫結*，而導致額外的作業在執行階段。 它也可能會讓您的應用程式發生執行階段錯誤。 例如，如果您指派<xref:System.Windows.Forms.Form>至`Object`變數，然後嘗試存取<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName>屬性，在執行階段擲回<xref:System.MemberAccessException>因為<xref:System.Windows.Forms.Form>類別不會公開`NameTable`屬性。</xref:System.Windows.Forms.Form> </xref:System.MemberAccessException> </xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName> </xref:System.Windows.Forms.Form>  
  
 如果是特定類型的變數宣告，編譯器可以執行*早期繫結*在編譯時期。 如此可改善效能，控制存取的特定型別、 成員以及您的程式碼更容易閱讀。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤識別碼︰** BC42017  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   可能的話，請宣告為特定類型的變數。  
  
## <a name="see-also"></a>另請參閱  
 [早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)   
 [物件變數宣告](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
