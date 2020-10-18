---
title: 類型 <type> 的運算式無法查詢
ms.date: 07/20/2015
f1_keywords:
- bc36593
- vbc36593
helpviewer_keywords:
- BC36593
ms.assetid: 6f1f5860-bf97-4885-9ebb-bc87d028095c
ms.openlocfilehash: d605243c213166f20592fdc440a3362f957ebbf2
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163060"
---
# <a name="bc36593-expression-of-type-type-is-not-queryable"></a><span data-ttu-id="dd5d0-102">BC36593：類型的運算式不可 \<type> 查詢</span><span class="sxs-lookup"><span data-stu-id="dd5d0-102">BC36593: Expression of type \<type> is not queryable</span></span>

<span data-ttu-id="dd5d0-103">型別的運算式 \<type> 無法查詢。</span><span class="sxs-lookup"><span data-stu-id="dd5d0-103">Expression of type \<type> is not queryable.</span></span> <span data-ttu-id="dd5d0-104">請確定您沒有遺漏元件參考及（或） LINQ 提供者的命名空間匯入。</span><span class="sxs-lookup"><span data-stu-id="dd5d0-104">Make sure you are not missing an assembly reference and/or namespace import for the LINQ provider.</span></span>

 <span data-ttu-id="dd5d0-105">可查詢的類型定義于 <xref:System.Linq> 、 <xref:System.Data.Linq> 和 <xref:System.Xml.Linq> 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="dd5d0-105">Queryable types are defined in the <xref:System.Linq>, <xref:System.Data.Linq>, and <xref:System.Xml.Linq> namespaces.</span></span> <span data-ttu-id="dd5d0-106">您必須匯入一或多個這些命名空間，才能執行 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="dd5d0-106">You must import one or more of these namespaces to perform LINQ queries.</span></span>

 <span data-ttu-id="dd5d0-107"><xref:System.Linq>命名空間可讓您使用 LINQ 查詢物件，例如集合和陣列。</span><span class="sxs-lookup"><span data-stu-id="dd5d0-107">The <xref:System.Linq> namespace enables you to query objects such as collections and arrays by using LINQ.</span></span>

 <span data-ttu-id="dd5d0-108"><xref:System.Data.Linq>命名空間可讓您使用 LINQ 查詢 ADO.NET 資料集和 SQL Server 資料庫。</span><span class="sxs-lookup"><span data-stu-id="dd5d0-108">The <xref:System.Data.Linq> namespace enables you to query ADO.NET Datasets and SQL Server databases by using LINQ.</span></span>

 <span data-ttu-id="dd5d0-109"><xref:System.Xml.Linq>命名空間可讓您使用 LINQ 查詢 xml，並在 Visual Basic 中使用 xml 功能。</span><span class="sxs-lookup"><span data-stu-id="dd5d0-109">The <xref:System.Xml.Linq> namespace enables you to query XML by using LINQ and to use XML features in Visual Basic.</span></span>

 <span data-ttu-id="dd5d0-110">**錯誤識別碼：** BC36593</span><span class="sxs-lookup"><span data-stu-id="dd5d0-110">**Error ID:** BC36593</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="dd5d0-111">更正這個錯誤</span><span class="sxs-lookup"><span data-stu-id="dd5d0-111">To correct this error</span></span>

1. <span data-ttu-id="dd5d0-112">將 `Import` <xref:System.Linq> 、 <xref:System.Data.Linq> 或命名空間的語句新增 <xref:System.Xml.Linq> 至程式碼檔案。</span><span class="sxs-lookup"><span data-stu-id="dd5d0-112">Add an `Import` statement for the <xref:System.Linq>, <xref:System.Data.Linq>, or <xref:System.Xml.Linq> namespace to your code file.</span></span> <span data-ttu-id="dd5d0-113">您也可以使用 [專案設計工具] 的 [ **參考** ] 頁面 ([我的 **專案** ]) 來匯入專案的命名空間。</span><span class="sxs-lookup"><span data-stu-id="dd5d0-113">You can also import namespaces for your project by using the **References** page of the Project Designer (**My Project**).</span></span>

2. <span data-ttu-id="dd5d0-114">確定您已識別為查詢來源的類型是可查詢的類型。</span><span class="sxs-lookup"><span data-stu-id="dd5d0-114">Ensure that the type that you have identified as the source of your query is a queryable type.</span></span> <span data-ttu-id="dd5d0-115">也就是實作為或的型別 <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Linq.IQueryable%601> 。</span><span class="sxs-lookup"><span data-stu-id="dd5d0-115">That is, a type that implements <xref:System.Collections.Generic.IEnumerable%601> or <xref:System.Linq.IQueryable%601>.</span></span>

## <a name="see-also"></a><span data-ttu-id="dd5d0-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd5d0-116">See also</span></span>

- <xref:System.Linq>
- <xref:System.Data.Linq>
- <xref:System.Xml.Linq>
- [<span data-ttu-id="dd5d0-117">Visual Basic 中的 LINQ 簡介</span><span class="sxs-lookup"><span data-stu-id="dd5d0-117">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="dd5d0-118">LINQ</span><span class="sxs-lookup"><span data-stu-id="dd5d0-118">LINQ</span></span>](../../programming-guide/language-features/linq/index.md)
- [<span data-ttu-id="dd5d0-119">XML</span><span class="sxs-lookup"><span data-stu-id="dd5d0-119">XML</span></span>](../../programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="dd5d0-120">References 與 Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="dd5d0-120">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="dd5d0-121">Imports 陳述式 (.NET 命名空間和類型)</span><span class="sxs-lookup"><span data-stu-id="dd5d0-121">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="dd5d0-122">專案設計工具，參考頁 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dd5d0-122">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
