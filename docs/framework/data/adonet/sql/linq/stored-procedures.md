---
title: 預存程序
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 9201965192f300de62679c1e5be75cf98a24e700
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33360592"
---
# <a name="stored-procedures"></a><span data-ttu-id="1914f-102">預存程序</span><span class="sxs-lookup"><span data-stu-id="1914f-102">Stored Procedures</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="1914f-103"> 使用物件模型中的方法，來代表在資料庫中的預存程序。</span><span class="sxs-lookup"><span data-stu-id="1914f-103"> uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="1914f-104">您可套用 <xref:System.Data.Linq.Mapping.FunctionAttribute> 屬性 (Attribute) 和 (視需要) 套用 <xref:System.Data.Linq.Mapping.ParameterAttribute> 屬性，將方法指定為預存程序。</span><span class="sxs-lookup"><span data-stu-id="1914f-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="1914f-105">如需詳細資訊，請參閱[LINQ to SQL 物件模型](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="1914f-105">For more information, see [The LINQ to SQL Object Model](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="1914f-106">使用 Visual Studio 的開發人員通常會使用[!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)]對應預存程序。</span><span class="sxs-lookup"><span data-stu-id="1914f-106">Developers using Visual Studio would typically use the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] to map stored procedures.</span></span> <span data-ttu-id="1914f-107">本節中的主題顯示自行撰寫程式碼時，如何在應用程式中形成和呼叫這些方法。</span><span class="sxs-lookup"><span data-stu-id="1914f-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1914f-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="1914f-108">In This Section</span></span>  
 [<span data-ttu-id="1914f-109">如何：傳回資料列集</span><span class="sxs-lookup"><span data-stu-id="1914f-109">How to: Return Rowsets</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-return-rowsets.md)  
 <span data-ttu-id="1914f-110">描述如何傳回資料列，以及顯示如何使用輸入參數。</span><span class="sxs-lookup"><span data-stu-id="1914f-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="1914f-111">如何：使用有參數的預存程序</span><span class="sxs-lookup"><span data-stu-id="1914f-111">How to: Use Stored Procedures that Take Parameters</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="1914f-112">描述如何使用輸入和輸出參數。</span><span class="sxs-lookup"><span data-stu-id="1914f-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="1914f-113">如何：使用與多個結果型式對應的預存程序</span><span class="sxs-lookup"><span data-stu-id="1914f-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="1914f-114">描述如何為在相同預存程序中傳回多個圖案做準備。</span><span class="sxs-lookup"><span data-stu-id="1914f-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="1914f-115">如何：使用與循序結果型式對應的預存程序</span><span class="sxs-lookup"><span data-stu-id="1914f-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="1914f-116">描述如何為已知傳回序列情況下的多個圖案做準備。</span><span class="sxs-lookup"><span data-stu-id="1914f-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="1914f-117">使用預存程序來自訂作業</span><span class="sxs-lookup"><span data-stu-id="1914f-117">Customizing Operations By Using Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="1914f-118">描述如何使用預存程序來實作插入、更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="1914f-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="1914f-119">以獨佔模式使用預存程序來自訂作業</span><span class="sxs-lookup"><span data-stu-id="1914f-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="1914f-120">描述如何只使用預存程序來實作插入、更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="1914f-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1914f-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="1914f-121">Related Sections</span></span>  
 [<span data-ttu-id="1914f-122">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="1914f-122">Programming Guide</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/programming-guide.md)  
 <span data-ttu-id="1914f-123">提供如何建立和使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件模型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="1914f-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="1914f-124">逐步解說：僅使用預存程序 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1914f-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="1914f-125">包含可說明如何在 Visual Basic 中使用預存程序的相關程序。</span><span class="sxs-lookup"><span data-stu-id="1914f-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="1914f-126">逐步解說：僅使用預存程序 (C#)</span><span class="sxs-lookup"><span data-stu-id="1914f-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="1914f-127">包含可說明如何在 C# 中使用預存程序的相關程序。</span><span class="sxs-lookup"><span data-stu-id="1914f-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>
