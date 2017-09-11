---
title: "開始使用 C# 中的 LINQ"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- LINQ [C#]
- queries [LINQ in C#]
- LINQ, C#
- queries [LINQ], LINQ in C#
ms.assetid: b8700c1f-05c9-4380-b6eb-e34c4da38e54
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 02a76889912e441cc0d1bcf27cb5e9421ef852ad
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="getting-started-with-linq-in-c"></a><span data-ttu-id="1fca6-102">開始使用 C# 中的 LINQ</span><span class="sxs-lookup"><span data-stu-id="1fca6-102">Getting Started with LINQ in C#</span></span>
<span data-ttu-id="1fca6-103">本節包含基本的背景資訊可協助您了解其餘 LINQ 文件和範例。</span><span class="sxs-lookup"><span data-stu-id="1fca6-103">This section contains basic background information that will help you understand the rest of the LINQ documentation and samples.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1fca6-104">本章節內容</span><span class="sxs-lookup"><span data-stu-id="1fca6-104">In This Section</span></span>  
 [<span data-ttu-id="1fca6-105">LINQ 查詢簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="1fca6-105">Introduction to LINQ Queries (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 <span data-ttu-id="1fca6-106">說明所有語言和資料來源通用的基本 LINQ 查詢作業，共分三個部分。</span><span class="sxs-lookup"><span data-stu-id="1fca6-106">Describes the three parts of the basic LINQ query operation that are common across all languages and data sources.</span></span>  
  
 [<span data-ttu-id="1fca6-107">LINQ 和泛型型別 (C#)</span><span class="sxs-lookup"><span data-stu-id="1fca6-107">LINQ and Generic Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-and-generic-types.md)  
 <span data-ttu-id="1fca6-108">提供 LINQ 使用的泛型型別簡介。</span><span class="sxs-lookup"><span data-stu-id="1fca6-108">Provides a brief introduction to generic types as they are used in LINQ.</span></span>  
  
 [<span data-ttu-id="1fca6-109">基本 LINQ 查詢作業</span><span class="sxs-lookup"><span data-stu-id="1fca6-109">Basic LINQ Query Operations</span></span>](../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)  
 <span data-ttu-id="1fca6-110">說明最常見的查詢作業類型及其在 C# 中的表示方式。</span><span class="sxs-lookup"><span data-stu-id="1fca6-110">Describes the most common types of query operations and how they are expressed in C#.</span></span>  
  
 [<span data-ttu-id="1fca6-111">使用 LINQ 轉換資料 (C#)</span><span class="sxs-lookup"><span data-stu-id="1fca6-111">Data Transformations with LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/data-transformations-with-linq.md)  
 <span data-ttu-id="1fca6-112">說明您可以針對查詢所擷取之資料進行轉換的各種方式。</span><span class="sxs-lookup"><span data-stu-id="1fca6-112">Describes the various ways that you can transform data retrieved in queries.</span></span>  
  
 [<span data-ttu-id="1fca6-113">LINQ 查詢作業中的型別關聯性</span><span class="sxs-lookup"><span data-stu-id="1fca6-113">Type Relationships in LINQ Query Operations</span></span>](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)  
 <span data-ttu-id="1fca6-114">說明這三個部分的 LINQ 查詢作業會如何保留及/或轉換類型。</span><span class="sxs-lookup"><span data-stu-id="1fca6-114">Describes how types are preserved and/or transformed in the three parts of a LINQ query operation</span></span>  
  
 [<span data-ttu-id="1fca6-115">LINQ 中的查詢語法及方法語法</span><span class="sxs-lookup"><span data-stu-id="1fca6-115">Query Syntax and Method Syntax in LINQ</span></span>](../../../../csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)  
 <span data-ttu-id="1fca6-116">針對方法語法和查詢語法這兩種表示 LINQ 查詢的方式進行比較。</span><span class="sxs-lookup"><span data-stu-id="1fca6-116">Compares method syntax and query syntax as two ways to express a LINQ query.</span></span>  
  
 [<span data-ttu-id="1fca6-117">支援 LINQ 的 C# 功能</span><span class="sxs-lookup"><span data-stu-id="1fca6-117">C# Features That Support LINQ</span></span>](../../../../csharp/programming-guide/concepts/linq/features-that-support-linq.md)  
 <span data-ttu-id="1fca6-118">說明 C# 3.0 中新增以支援 LINQ 的語言建構。</span><span class="sxs-lookup"><span data-stu-id="1fca6-118">Describes the language constructs added in C# 3.0 that support LINQ.</span></span>  
  
 [<span data-ttu-id="1fca6-119">逐步解說：在 C# 中撰寫查詢</span><span class="sxs-lookup"><span data-stu-id="1fca6-119">Walkthrough: Writing Queries in C#</span></span>](../../../../csharp/programming-guide/concepts/linq/walkthrough-writing-queries-linq.md)  
 <span data-ttu-id="1fca6-120">建立 C# LINQ 專案、新增簡單資料來源及執行一些基本查詢作業的逐步指示。</span><span class="sxs-lookup"><span data-stu-id="1fca6-120">Step-by-step instructions for creating a C# LINQ project, adding a simple data source, and performing some basic query operations.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1fca6-121">相關章節</span><span class="sxs-lookup"><span data-stu-id="1fca6-121">Related Sections</span></span>  
 [<span data-ttu-id="1fca6-122">Language-Integrated Query (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="1fca6-122">Language-Integrated Query (LINQ) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/index.md)  
 <span data-ttu-id="1fca6-123">提供說明 LINQ 技術的主題連結。</span><span class="sxs-lookup"><span data-stu-id="1fca6-123">Provides links to topics that explain the LINQ technologies.</span></span>  
  
 [<span data-ttu-id="1fca6-124">LINQ 查詢運算式</span><span class="sxs-lookup"><span data-stu-id="1fca6-124">LINQ Query Expressions</span></span>](../../../../csharp/programming-guide/linq-query-expressions/index.md)  
 <span data-ttu-id="1fca6-125">包含 LINQ 的查詢概觀，並提供其他資源連結。</span><span class="sxs-lookup"><span data-stu-id="1fca6-125">Includes an overview of queries in LINQ and provides links to additional resources.</span></span>  
  
 [<span data-ttu-id="1fca6-126">LINQ 的 Visual Studio IDE 和工具支援 (C#)</span><span class="sxs-lookup"><span data-stu-id="1fca6-126">Visual Studio IDE and Tools Support for LINQ (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/visual-studio-ide-and-tools-support-for-linq.md)  
 <span data-ttu-id="1fca6-127">說明 Visual Studio 環境中可用來設計、編碼和偵錯啟用 LINQ 之應用程式的工具。</span><span class="sxs-lookup"><span data-stu-id="1fca6-127">Describes tools available in the Visual Studio environment for designing, coding, and debugging LINQ-enabled application.</span></span>  
  
 [<span data-ttu-id="1fca6-128">標準查詢運算子概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="1fca6-128">Standard Query Operators Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)  
 <span data-ttu-id="1fca6-129">介紹 LINQ 中使用的標準方法。</span><span class="sxs-lookup"><span data-stu-id="1fca6-129">Introduces the standard methods used in LINQ.</span></span>  
  
 [<span data-ttu-id="1fca6-130">使用 Visual Basic 撰寫 LINQ 入門</span><span class="sxs-lookup"><span data-stu-id="1fca6-130">Getting Started with LINQ in Visual Basic</span></span>](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)  
 <span data-ttu-id="1fca6-131">提供有關如何搭配 Visual Basic 使用 LINQ 的主題連結。</span><span class="sxs-lookup"><span data-stu-id="1fca6-131">Provides links to topics about using LINQ with Visual Basic.</span></span>

