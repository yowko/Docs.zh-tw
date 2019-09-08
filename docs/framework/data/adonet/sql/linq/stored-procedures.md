---
title: 預存程序
ms.date: 03/30/2017
ms.assetid: 4d23dd7a-a85f-44ff-a717-af7d0950c0fc
ms.openlocfilehash: 80ea105eef33ebb2a0e52d91a631258400ea3dff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792487"
---
# <a name="stored-procedures"></a><span data-ttu-id="561cc-102">預存程序</span><span class="sxs-lookup"><span data-stu-id="561cc-102">Stored Procedures</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="561cc-103">使用物件模型中的方法，表示資料庫中的預存程式。</span><span class="sxs-lookup"><span data-stu-id="561cc-103">uses methods in your object model to represent stored procedures in the database.</span></span> <span data-ttu-id="561cc-104">您可套用 <xref:System.Data.Linq.Mapping.FunctionAttribute> 屬性 (Attribute) 和 (視需要) 套用 <xref:System.Data.Linq.Mapping.ParameterAttribute> 屬性，將方法指定為預存程序。</span><span class="sxs-lookup"><span data-stu-id="561cc-104">You designate methods as stored procedures by applying the <xref:System.Data.Linq.Mapping.FunctionAttribute> attribute and, where required, the <xref:System.Data.Linq.Mapping.ParameterAttribute> attribute.</span></span> <span data-ttu-id="561cc-105">如需詳細資訊，請參閱[LINQ to SQL 物件模型](the-linq-to-sql-object-model.md)。</span><span class="sxs-lookup"><span data-stu-id="561cc-105">For more information, see [The LINQ to SQL Object Model](the-linq-to-sql-object-model.md).</span></span>  
  
 <span data-ttu-id="561cc-106">使用 Visual Studio 的開發人員通常會使用物件關聯式設計工具來對應預存程式。</span><span class="sxs-lookup"><span data-stu-id="561cc-106">Developers using Visual Studio would typically use the Object Relational Designer to map stored procedures.</span></span> <span data-ttu-id="561cc-107">本節中的主題顯示自行撰寫程式碼時，如何在應用程式中形成和呼叫這些方法。</span><span class="sxs-lookup"><span data-stu-id="561cc-107">The topics in this section show how to form and call these methods in your application if you write the code yourself.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="561cc-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="561cc-108">In This Section</span></span>  
 [<span data-ttu-id="561cc-109">如何：傳回資料列集</span><span class="sxs-lookup"><span data-stu-id="561cc-109">How to: Return Rowsets</span></span>](how-to-return-rowsets.md)  
 <span data-ttu-id="561cc-110">描述如何傳回資料列，以及顯示如何使用輸入參數。</span><span class="sxs-lookup"><span data-stu-id="561cc-110">Describes how to return rows of data and shows how to use an input parameter.</span></span>  
  
 [<span data-ttu-id="561cc-111">如何：使用採用參數的預存程式</span><span class="sxs-lookup"><span data-stu-id="561cc-111">How to: Use Stored Procedures that Take Parameters</span></span>](how-to-use-stored-procedures-that-take-parameters.md)  
 <span data-ttu-id="561cc-112">描述如何使用輸入和輸出參數。</span><span class="sxs-lookup"><span data-stu-id="561cc-112">Describes how to use input and output parameters.</span></span>  
  
 [<span data-ttu-id="561cc-113">如何：針對多個結果圖形使用對應的預存程式</span><span class="sxs-lookup"><span data-stu-id="561cc-113">How to: Use Stored Procedures Mapped for Multiple Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-multiple-result-shapes.md)  
 <span data-ttu-id="561cc-114">描述如何為在相同預存程序中傳回多個圖案做準備。</span><span class="sxs-lookup"><span data-stu-id="561cc-114">Describes how to provide for returns of multiple shapes in the same stored procedure.</span></span>  
  
 [<span data-ttu-id="561cc-115">如何：針對順序結果圖形使用對應的預存程式</span><span class="sxs-lookup"><span data-stu-id="561cc-115">How to: Use Stored Procedures Mapped for Sequential Result Shapes</span></span>](how-to-use-stored-procedures-mapped-for-sequential-result-shapes.md)  
 <span data-ttu-id="561cc-116">描述如何為已知傳回序列情況下的多個圖案做準備。</span><span class="sxs-lookup"><span data-stu-id="561cc-116">Describes how to provide for multiple shapes where the return sequence is known.</span></span>  
  
 [<span data-ttu-id="561cc-117">使用預存程序來自訂作業</span><span class="sxs-lookup"><span data-stu-id="561cc-117">Customizing Operations By Using Stored Procedures</span></span>](customizing-operations-by-using-stored-procedures.md)  
 <span data-ttu-id="561cc-118">描述如何使用預存程序來實作插入、更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="561cc-118">Describes how to use stored procedures to implement insert, update, and delete operations.</span></span>  
  
 [<span data-ttu-id="561cc-119">以獨佔模式使用預存程序來自訂作業</span><span class="sxs-lookup"><span data-stu-id="561cc-119">Customizing Operations by Using Stored Procedures Exclusively</span></span>](customizing-operations-by-using-stored-procedures-exclusively.md)  
 <span data-ttu-id="561cc-120">描述如何只使用預存程序來實作插入、更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="561cc-120">Describes how to use nothing but stored procedures to implement insert, update, and delete operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="561cc-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="561cc-121">Related Sections</span></span>  
 [<span data-ttu-id="561cc-122">程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="561cc-122">Programming Guide</span></span>](programming-guide.md)  
 <span data-ttu-id="561cc-123">提供如何建立和使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 物件模型的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="561cc-123">Provides information about how to create and use your [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] object model.</span></span>  
  
 [<span data-ttu-id="561cc-124">逐步解說：僅使用預存程式（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="561cc-124">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>](walkthrough-using-only-stored-procedures-visual-basic.md)  
 <span data-ttu-id="561cc-125">包含可說明如何在 Visual Basic 中使用預存程序的相關程序。</span><span class="sxs-lookup"><span data-stu-id="561cc-125">Includes procedures that illustrate how to use stored procedures in Visual Basic.</span></span>  
  
 [<span data-ttu-id="561cc-126">逐步解說：僅使用預存程式C#（）</span><span class="sxs-lookup"><span data-stu-id="561cc-126">Walkthrough: Using Only Stored Procedures (C#)</span></span>](walkthrough-using-only-stored-procedures-csharp.md)  
 <span data-ttu-id="561cc-127">包含可說明如何在 C# 中使用預存程序的相關程序。</span><span class="sxs-lookup"><span data-stu-id="561cc-127">Includes procedures that illustrate how to use stored procedures in C#.</span></span>
