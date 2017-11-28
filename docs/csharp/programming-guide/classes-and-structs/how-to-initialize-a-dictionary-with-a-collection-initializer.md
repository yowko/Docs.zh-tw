---
title: "如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8b8de5fb85a839d52ad00ad552ef823d9817e9b7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="11e08-102">如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="11e08-102">How to: Initialize a Dictionary with a Collection Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="11e08-103"><xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> 方法會採用兩個參數，一個針對索引鍵，另一個針對值。</span><span class="sxs-lookup"><span data-stu-id="11e08-103">A <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="11e08-104">若要初始化 <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add\` 方法採用多個參數的任何集合，請將每個參數集以括號括住，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="11e08-104">To initialize a <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add\` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11e08-105">範例</span><span class="sxs-lookup"><span data-stu-id="11e08-105">Example</span></span>  
 <span data-ttu-id="11e08-106">在下列程式碼範例中，<xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName\` 的執行個體進行初始化。</span><span class="sxs-lookup"><span data-stu-id="11e08-106">In the following code example, a <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName\`.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]  
  
 <span data-ttu-id="11e08-107">請注意，該集合的每個項目中都有兩組括號。</span><span class="sxs-lookup"><span data-stu-id="11e08-107">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="11e08-108">最內層的括號會括住 `StudentName` 的物件初始設定式，最外層的括號會括住機碼值組，這組值會新增至 `students`<xref:System.Collections.Generic.Dictionary\`2>。</span><span class="sxs-lookup"><span data-stu-id="11e08-108">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students`<xref:System.Collections.Generic.Dictionary\`2>.</span></span> <span data-ttu-id="11e08-109">最後，會以括號括住目錄的整個集合初始設定式。</span><span class="sxs-lookup"><span data-stu-id="11e08-109">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="11e08-110">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="11e08-110">Compiling the Code</span></span>  
 <span data-ttu-id="11e08-111">若要執行此程式碼，請將該類別複製並貼到 [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)] 中所建立的 Visual C# 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="11e08-111">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="11e08-112">根據預設，此專案是以 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 3.5 版為目標，且有 System.Core.dll 的參考，以及 System.Linq 的 using 指示詞。</span><span class="sxs-lookup"><span data-stu-id="11e08-112">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="11e08-113">如果專案中遺漏上述一或多個需求，您可以手動新增這些需求。</span><span class="sxs-lookup"><span data-stu-id="11e08-113">If one or more of these requirements are missing from the project, you can add them manually.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e08-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11e08-114">See Also</span></span>  
 [<span data-ttu-id="11e08-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="11e08-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="11e08-116">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="11e08-116">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
