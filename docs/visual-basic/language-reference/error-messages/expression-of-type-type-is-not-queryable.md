---
title: 類型 <type> 的運算式無法查詢
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: 121c0a95a3a6bb695d9c73347c733cba215a0de4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61801617"
---
# <a name="expression-of-type-type-is-not-queryable"></a><span data-ttu-id="3c4bb-102">型別的運算式\<類型 > 不是可查詢</span><span class="sxs-lookup"><span data-stu-id="3c4bb-102">Expression of type \<type> is not queryable</span></span>
<span data-ttu-id="3c4bb-103">型別的運算式\<類型 > 不是可供查詢。</span><span class="sxs-lookup"><span data-stu-id="3c4bb-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="3c4bb-104">請確定您未遺漏組件參考和/或命名空間匯入 LINQ 提供者。</span><span class="sxs-lookup"><span data-stu-id="3c4bb-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>  
  
 <span data-ttu-id="3c4bb-105">中所定義的可查詢型別<xref:System.Linq>， <xref:System.Data.Linq>，和<xref:System.Xml.Linq>命名空間。</span><span class="sxs-lookup"><span data-stu-id="3c4bb-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="3c4bb-106">您必須匯入一或多個命名空間，以執行 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="3c4bb-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>  
  
 <span data-ttu-id="3c4bb-107"><xref:System.Linq>命名空間可讓您查詢物件，例如集合和陣列使用 LINQ。</span><span class="sxs-lookup"><span data-stu-id="3c4bb-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>  
  
 <span data-ttu-id="3c4bb-108"><xref:System.Data.Linq>命名空間可讓您使用 LINQ 查詢 ADO.NET 資料集和 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="3c4bb-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>  
  
 <span data-ttu-id="3c4bb-109"><xref:System.Xml.Linq>命名空間可讓您查詢 XML 使用 LINQ 和 Visual Basic 中使用 XML 功能。</span><span class="sxs-lookup"><span data-stu-id="3c4bb-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>  
  
 <span data-ttu-id="3c4bb-110">**錯誤 ID:** BC36593</span><span class="sxs-lookup"><span data-stu-id="3c4bb-110">**Error ID:** BC36593</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3c4bb-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="3c4bb-111">To correct this error</span></span>  
  
1. <span data-ttu-id="3c4bb-112">新增`Import`陳述式<xref:System.Linq>， <xref:System.Data.Linq>，或<xref:System.Xml.Linq>程式碼檔案的命名空間。</span><span class="sxs-lookup"><span data-stu-id="3c4bb-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="3c4bb-113">您也可以匯入命名空間為您的專案使用**參考**頁面的 專案設計工具 (**我的專案**)。</span><span class="sxs-lookup"><span data-stu-id="3c4bb-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>  
  
2. <span data-ttu-id="3c4bb-114">請確定您已識別為您的查詢的來源是可查詢類型的類型。</span><span class="sxs-lookup"><span data-stu-id="3c4bb-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="3c4bb-115">也就是型別可實作<xref:System.Collections.Generic.IEnumerable%601>或<xref:System.Linq.IQueryable%601>。</span><span class="sxs-lookup"><span data-stu-id="3c4bb-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c4bb-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c4bb-116">See also</span></span>

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [<span data-ttu-id="3c4bb-117">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="3c4bb-117">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="3c4bb-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="3c4bb-118">LINQ</span></span>](../../../visual-basic/programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="3c4bb-119">XML</span><span class="sxs-lookup"><span data-stu-id="3c4bb-119">XML</span></span>](../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="3c4bb-120">參考和 Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="3c4bb-120">References and the Imports Statement</span></span>](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="3c4bb-121">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="3c4bb-121">Imports Statement (.NET Namespace and Type)</span></span>](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="3c4bb-122">專案設計工具、參考頁面 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3c4bb-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
