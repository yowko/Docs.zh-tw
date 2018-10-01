---
title: 如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: ca2f508e5500cc135b2712362bcfb71778a664c1
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44227333"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="a5bde-102">如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="a5bde-102">How to initialize a dictionary with a collection initializer (C# Programming Guide)</span></span>

<span data-ttu-id="a5bde-103"><xref:System.Collections.Generic.Dictionary%602> 包含索引鍵/值組的集合。</span><span class="sxs-lookup"><span data-stu-id="a5bde-103">A <xref:System.Collections.Generic.Dictionary%602> contains a collection of key/value pairs.</span></span> <span data-ttu-id="a5bde-104">其 <xref:System.Collections.Generic.Dictionary%602.Add*> 方法採用兩個參數，其中之一供索引鍵之用，而另一個則供值之用。</span><span class="sxs-lookup"><span data-stu-id="a5bde-104">Its <xref:System.Collections.Generic.Dictionary%602.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="a5bde-105">若要初始化 <xref:System.Collections.Generic.Dictionary%602> 或任何其 `Add` 方法採用多重參數的所有集合，請將每個參數集以括號括住，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a5bde-105">To initialize a <xref:System.Collections.Generic.Dictionary%602>, or any collection whose `Add` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>

## <a name="example"></a><span data-ttu-id="a5bde-106">範例</span><span class="sxs-lookup"><span data-stu-id="a5bde-106">Example</span></span>

<span data-ttu-id="a5bde-107">在下列程式碼範例中，<xref:System.Collections.Generic.Dictionary%602> 會使用類型 `StudentName` 的執行個體進行初始化。</span><span class="sxs-lookup"><span data-stu-id="a5bde-107">In the following code example, a <xref:System.Collections.Generic.Dictionary%602> is initialized with instances of type `StudentName`.</span></span>  
  
[!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]

<span data-ttu-id="a5bde-108">請注意，該集合的每個項目中都有兩組括號。</span><span class="sxs-lookup"><span data-stu-id="a5bde-108">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="a5bde-109">最內層括號會括住 `StudentName` 的物件初始設定式，最外層括號會括住機碼值組，這組值會新增至 `students` <xref:System.Collections.Generic.Dictionary%602>。</span><span class="sxs-lookup"><span data-stu-id="a5bde-109">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students` <xref:System.Collections.Generic.Dictionary%602>.</span></span> <span data-ttu-id="a5bde-110">最後，會以括號括住目錄的整個集合初始設定式。</span><span class="sxs-lookup"><span data-stu-id="a5bde-110">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>

## <a name="compiling-the-code"></a><span data-ttu-id="a5bde-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="a5bde-111">Compiling the code</span></span>

<span data-ttu-id="a5bde-112">若要執行此程式碼，請將該類別複製並貼到已在 Visual Studio 中建立的 Visual C# 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="a5bde-112">To run this code, copy and paste the class into a Visual C# console application project that has been created in Visual Studio.</span></span> <span data-ttu-id="a5bde-113">根據預設，此專案是以 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 3.5 版為目標，且有 System.Core.dll 的參考，以及 System.Linq 的 using 指示詞。</span><span class="sxs-lookup"><span data-stu-id="a5bde-113">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="a5bde-114">如果專案中遺漏上述一或多個需求，您可以手動新增這些需求。</span><span class="sxs-lookup"><span data-stu-id="a5bde-114">If one or more of these requirements are missing from the project, you can add them manually.</span></span>

## <a name="see-also"></a><span data-ttu-id="a5bde-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5bde-115">See also</span></span>

- [<span data-ttu-id="a5bde-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a5bde-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a5bde-117">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="a5bde-117">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
