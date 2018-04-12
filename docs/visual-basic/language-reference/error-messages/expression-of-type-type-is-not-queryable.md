---
title: 型別的運算式&lt;類型&gt;不是可查詢
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3f2b98bf48f0b3965929f9211c2944ff97754f23
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a>型別的運算式&lt;類型&gt;不是可查詢
型別的運算式\<類型 > 不是可供查詢。 請確定您沒有遺漏組件參考和/或命名空間匯入的 LINQ 提供者。  
  
 可查詢類型都定義在<xref:System.Linq>， <xref:System.Data.Linq>，和<xref:System.Xml.Linq>命名空間。 您必須匯入一或多個命名空間，以執行 LINQ 查詢。  
  
 <xref:System.Linq>命名空間可讓您查詢物件，例如集合和陣列使用 LINQ。  
  
 <xref:System.Data.Linq>命名空間可讓您使用 LINQ 查詢 ADO.NET 資料集和 SQL Server 資料庫。  
  
 <xref:System.Xml.Linq>命名空間可讓您查詢 XML 使用 LINQ 和 Visual Basic 中使用 XML 功能。  
  
 **錯誤 ID:** BC36593  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  新增`Import`陳述式<xref:System.Linq>， <xref:System.Data.Linq>，或<xref:System.Xml.Linq>程式碼檔案的命名空間。 您也可以匯入命名空間為您的專案使用**參考**頁面的 專案設計工具 (**我的專案**)。  
  
2.  請確定您已識別為查詢的來源是可查詢的型別類型。 也就是說，型別可實作<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Linq>  
 <xref:System.Data.Linq>  
 <xref:System.Xml.Linq>  
 [Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [參考和 Imports 陳述式](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)  
 [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [專案設計工具、參考頁面 (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
