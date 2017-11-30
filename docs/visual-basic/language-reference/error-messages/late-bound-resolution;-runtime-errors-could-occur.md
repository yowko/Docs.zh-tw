---
title: "晚期繫結程序解析; 可能發生執行階段錯誤"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
helpviewer_keywords: BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d01164914b484ef689654f048a8743f3c2eb669
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>晚期繫結程序解析; 可能發生執行階段錯誤
物件變數指派給變數宣告為[物件資料類型](../../../visual-basic/language-reference/data-types/object-data-type.md)。  
  
 當您將變數宣告為`Object`，編譯器必須執行*晚期繫結*，因而導致執行階段的額外作業。 它也可能會讓您的應用程式發生執行階段錯誤。 例如，如果您指派<xref:System.Windows.Forms.Form>至`Object`變數，然後嘗試存取<xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=nameWithType>屬性，執行階段會擲回<xref:System.MemberAccessException>因為<xref:System.Windows.Forms.Form>類別並未公開`NameTable`屬性。  
  
 如果是特定類型的變數宣告，編譯器可以執行*早期繫結*在編譯時間。 如此可改善效能、 控制存取特定類型的成員以及您的程式碼更容易閱讀。  
  
 根據預設，這個訊息是一個警告。 如需隱藏警告或將警告視為錯誤的相關資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。  
  
 **錯誤 ID:** BC42017  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
-   可能的話，宣告為特定類型的變數。  
  
## <a name="see-also"></a>另請參閱  
 [早期和晚期繫結](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)  
 [物件變數宣告](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
