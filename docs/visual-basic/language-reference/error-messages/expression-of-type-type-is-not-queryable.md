---
title: "型別的運算式&lt;類型&gt;不是可查詢 |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36593
- vbc36593
dev_langs:
- VB
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
caps.latest.revision: 5
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 84563c7339ffe7415017280d74a13d6501236da5
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="expression-of-type-lttypegt-is-not-queryable"></a><span data-ttu-id="78166-102">型別的運算式&lt;類型&gt;不是可查詢</span><span class="sxs-lookup"><span data-stu-id="78166-102">Expression of type &lt;type&gt; is not queryable</span></span>
<span data-ttu-id="78166-103">型別的運算式\<類型 > 不是可查詢。</span><span class="sxs-lookup"><span data-stu-id="78166-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="78166-104">請確認未遺漏組件參考和/或命名空間匯入 LINQ 提供者。</span><span class="sxs-lookup"><span data-stu-id="78166-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="78166-105">可查詢的類型定義於<xref:System.Linq>， <xref:System.Data.Linq>，和<xref:System.Xml.Linq>命名空間。</xref:System.Xml.Linq> </xref:System.Data.Linq> </xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="78166-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="78166-106">您必須匯入一或多個命名空間，以執行 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="78166-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="78166-107"><xref:System.Linq>命名空間可讓您查詢物件，例如集合和陣列使用 LINQ。</xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="78166-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="78166-108"><xref:System.Data.Linq>命名空間可讓您使用 LINQ 查詢 ADO.NET 資料集和 SQL Server 資料庫。</xref:System.Data.Linq></span><span class="sxs-lookup"><span data-stu-id="78166-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="78166-109"><xref:System.Xml.Linq>命名空間可讓您查詢 XML 使用 LINQ 和 Visual Basic 中使用 XML 功能。</xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="78166-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="78166-110">**錯誤識別碼︰** BC36593</span><span class="sxs-lookup"><span data-stu-id="78166-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="78166-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="78166-111">To correct this error</span></span>  
  
1.  <span data-ttu-id="78166-112">新增`Import`陳述式<xref:System.Linq>， <xref:System.Data.Linq>，或<xref:System.Xml.Linq>程式碼檔案的命名空間。</xref:System.Xml.Linq> </xref:System.Data.Linq> </xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="78166-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="78166-113">您也可以匯入命名空間為您的專案使用**參考**頁面的 專案設計工具 (**我的專案**)。</span><span class="sxs-lookup"><span data-stu-id="78166-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2.  <span data-ttu-id="78166-114">請確定您已識別為查詢的來源是可查詢類型的類型。</span><span class="sxs-lookup"><span data-stu-id="78166-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="78166-115">也就是實作<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>.</xref:System.Linq.IQueryable%601></xref:System.Collections.Generic.IEnumerable%601>類型</span><span class="sxs-lookup"><span data-stu-id="78166-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78166-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78166-116">See Also</span></span>  
 <span data-ttu-id="78166-117"><xref:System.Linq></xref:System.Linq></span><span class="sxs-lookup"><span data-stu-id="78166-117"><xref:System.Linq></span></span>   
 <span data-ttu-id="78166-118"><xref:System.Data.Linq></xref:System.Data.Linq></span><span class="sxs-lookup"><span data-stu-id="78166-118"><xref:System.Data.Linq></span></span>   
 <span data-ttu-id="78166-119"><xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="78166-119"><xref:System.Xml.Linq></span></span>   
<span data-ttu-id="78166-120"> [在 Visual Basic 中的 LINQ 簡介](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span><span class="sxs-lookup"><span data-stu-id="78166-120"> [Introduction to LINQ in Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md) </span></span>  
<span data-ttu-id="78166-121"> [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span><span class="sxs-lookup"><span data-stu-id="78166-121"> [LINQ](../../../visual-basic/programming-guide/language-features/linq/index.md) </span></span>  
<span data-ttu-id="78166-122"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="78166-122"> [XML](../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="78166-123"> [參考和 Imports 陳述式](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span><span class="sxs-lookup"><span data-stu-id="78166-123"> [References and the Imports Statement](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md) </span></span>  
<span data-ttu-id="78166-124"> [Imports 陳述式 (.NET 命名空間和類型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span><span class="sxs-lookup"><span data-stu-id="78166-124"> [Imports Statement (.NET Namespace and Type)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) </span></span>  
<span data-ttu-id="78166-125"> [專案設計工具、參考頁面 (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span><span class="sxs-lookup"><span data-stu-id="78166-125"> [References Page, Project Designer (Visual Basic)](https://docs.microsoft.com/visualstudio/ide/reference/references-page-project-designer-visual-basic)</span></span>
