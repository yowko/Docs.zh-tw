---
title: XML 純功能性轉換 (C#)
ms.date: 07/20/2015
ms.assetid: 97e8e582-eb3d-4756-bbfb-0899eb688ae4
ms.openlocfilehash: e05c6167973b2342aafd51aad7d9102db9e94ae0
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47209756"
---
# <a name="pure-functional-transformations-of-xml-c"></a><span data-ttu-id="f6176-102">XML 純功能性轉換 (C#)</span><span class="sxs-lookup"><span data-stu-id="f6176-102">Pure Functional Transformations of XML (C#)</span></span>
<span data-ttu-id="f6176-103">本節提供 XML 的功能性轉換教學課程。</span><span class="sxs-lookup"><span data-stu-id="f6176-103">This section provides a functional transformation tutorial for XML.</span></span> <span data-ttu-id="f6176-104">這包含您必須了解之主要概念和語言建構以使用功能性轉換的說明，以及使用功能性轉換以管理 XML 文件的範例。</span><span class="sxs-lookup"><span data-stu-id="f6176-104">This includes explanations of the main concepts and language constructs that you must understand to use functional transformations, and examples of using functional transformations to manipulate an XML document.</span></span> <span data-ttu-id="f6176-105">雖然這個教學課程提供 LINQ to XML 程式碼範例，但是所有基礎概念也適用於其他 LINQ 技術。</span><span class="sxs-lookup"><span data-stu-id="f6176-105">Although this tutorial provides LINQ to XML code examples, all of the underlying concepts also apply to other LINQ technologies.</span></span>  
  
 <span data-ttu-id="f6176-106">[教學課程：管理 WordprocessingML 文件中的內容 (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) 教學課程提供一系列的範例，每個範例都是根據前一個範例所建置。</span><span class="sxs-lookup"><span data-stu-id="f6176-106">The [Tutorial: Manipulating Content in a WordprocessingML Document (C#)](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md) tutorial provides a series of examples, each building on the previous one.</span></span> <span data-ttu-id="f6176-107">這些範例會示範純功能性轉換方法以管理 XML。</span><span class="sxs-lookup"><span data-stu-id="f6176-107">These examples demonstrate the pure functional transformational approach to manipulating XML.</span></span>  
  
 <span data-ttu-id="f6176-108">本教學課程假設您具備 C# 的使用知識。</span><span class="sxs-lookup"><span data-stu-id="f6176-108">This tutorial assumes a working knowledge of C#.</span></span> <span data-ttu-id="f6176-109">在此教學課程中不會提供語言建構的詳細語意，但是會適當地提供語言文件的連結。</span><span class="sxs-lookup"><span data-stu-id="f6176-109">Detailed semantics of the language constructs are not provided in this tutorial, but links are provided to the language documentation as appropriate.</span></span>  
  
 <span data-ttu-id="f6176-110">同時也假設具備資訊科學基本概念與 XML (包括 XML 命名空間) 的實用知識。</span><span class="sxs-lookup"><span data-stu-id="f6176-110">A working knowledge of basic computer science concepts and XML, including XML namespaces, is also assumed.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f6176-111">本節內容</span><span class="sxs-lookup"><span data-stu-id="f6176-111">In This Section</span></span>  
  
|<span data-ttu-id="f6176-112">主題</span><span class="sxs-lookup"><span data-stu-id="f6176-112">Topic</span></span>|<span data-ttu-id="f6176-113">描述</span><span class="sxs-lookup"><span data-stu-id="f6176-113">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="f6176-114">純功能性轉換簡介 (C#)</span><span class="sxs-lookup"><span data-stu-id="f6176-114">Introduction to Pure Functional Transformations (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)|<span data-ttu-id="f6176-115">描述功能性轉換並定義相關的術語。</span><span class="sxs-lookup"><span data-stu-id="f6176-115">Describes functional transformations and defines the relevant terminology.</span></span>|  
|[<span data-ttu-id="f6176-116">教學課程：將查詢鏈結在一起 (C#)</span><span class="sxs-lookup"><span data-stu-id="f6176-116">Tutorial: Chaining Queries Together (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-chaining-queries-together.md)|<span data-ttu-id="f6176-117">詳細描述延遲評估以及延後執行。</span><span class="sxs-lookup"><span data-stu-id="f6176-117">Describes lazy evaluation and deferred execution in detail.</span></span>|  
|[<span data-ttu-id="f6176-118">教學課程：管理 WordprocessingML 文件中的內容 (C#)</span><span class="sxs-lookup"><span data-stu-id="f6176-118">Tutorial: Manipulating Content in a WordprocessingML Document (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/tutorial-manipulating-content-in-a-wordprocessingml-document.md)|<span data-ttu-id="f6176-119">示範功能性轉換的教學課程。</span><span class="sxs-lookup"><span data-stu-id="f6176-119">A tutorial that demonstrates a functional transformation.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f6176-120">請參閱</span><span class="sxs-lookup"><span data-stu-id="f6176-120">See Also</span></span>

- [<span data-ttu-id="f6176-121">查詢 XML 樹狀結構 (C#)</span><span class="sxs-lookup"><span data-stu-id="f6176-121">Querying XML Trees (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/querying-xml-trees.md)
