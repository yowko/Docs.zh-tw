---
title: "如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
caps.latest.revision: 10
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
ms.openlocfilehash: 41d6a9934daaa1274901e20de58cfd480c904bfa
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a><span data-ttu-id="01ec3-102">如何：使用集合初始設定式來初始化字典 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="01ec3-102">How to: Initialize a Dictionary with a Collection Initializer (C# Programming Guide)</span></span>
<span data-ttu-id="01ec3-103"><xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> 方法會採用兩個參數，一個針對索引鍵，另一個針對值。</span><span class="sxs-lookup"><span data-stu-id="01ec3-103">A <xref:System.Collections.Generic.Dictionary`2> contains a collection of key/value pairs. Its <xref:System.Collections.Generic.Dictionary`2.Add*> method takes two parameters, one for the key and one for the value.</span></span> <span data-ttu-id="01ec3-104">若要初始化 <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add\` 方法採用多個參數的任何集合，請將每個參數集以括號括住，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="01ec3-104">To initialize a <xref:System.Collections.Generic.Dictionary`2>, or any collection whose `Add\` method takes multiple parameters, enclose each set of parameters in braces as shown in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01ec3-105">範例</span><span class="sxs-lookup"><span data-stu-id="01ec3-105">Example</span></span>  
 <span data-ttu-id="01ec3-106">在下列程式碼範例中，<xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName\` 的執行個體進行初始化。</span><span class="sxs-lookup"><span data-stu-id="01ec3-106">In the following code example, a <xref:System.Collections.Generic.Dictionary`2> is initialized with instances of type `StudentName\`.</span></span>  
  
 <span data-ttu-id="01ec3-107">[!code-cs[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="01ec3-107">[!code-cs[csProgGuideLINQ#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-initialize-a-dictionary-with-a-collection-initializer_1.cs)]</span></span>  
  
 <span data-ttu-id="01ec3-108">請注意，該集合的每個項目中都有兩組括號。</span><span class="sxs-lookup"><span data-stu-id="01ec3-108">Note the two pairs of braces in each element of the collection.</span></span> <span data-ttu-id="01ec3-109">最內層的括號會括住 `StudentName` 的物件初始設定式，最外層的括號會括住機碼值組，這組值會新增至 `students`<xref:System.Collections.Generic.Dictionary\`2>。</span><span class="sxs-lookup"><span data-stu-id="01ec3-109">The innermost braces enclose the object initializer for the `StudentName`, and the outermost braces enclose the initializer for the key/value pair that will be added to the `students`<xref:System.Collections.Generic.Dictionary\`2>.</span></span> <span data-ttu-id="01ec3-110">最後，會以括號括住目錄的整個集合初始設定式。</span><span class="sxs-lookup"><span data-stu-id="01ec3-110">Finally, the whole collection initializer for the dictionary is enclosed in braces.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="01ec3-111">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="01ec3-111">Compiling the Code</span></span>  
 <span data-ttu-id="01ec3-112">若要執行此程式碼，請將該類別複製並貼到 [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)] 中所建立的 Visual C# 主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="01ec3-112">To run this code, copy and paste the class into a Visual C# console application project that has been created in [!INCLUDE[vs_current_short](~/includes/vs-current-short-md.md)].</span></span> <span data-ttu-id="01ec3-113">根據預設，此專案是以 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] 3.5 版為目標，且有 System.Core.dll 的參考，以及 System.Linq 的 using 指示詞。</span><span class="sxs-lookup"><span data-stu-id="01ec3-113">By default, this project targets version 3.5 of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], and it has a reference to System.Core.dll and a using directive for System.Linq.</span></span> <span data-ttu-id="01ec3-114">如果專案中遺漏上述一或多個需求，您可以手動新增這些需求。</span><span class="sxs-lookup"><span data-stu-id="01ec3-114">If one or more of these requirements are missing from the project, you can add them manually.</span></span>   
  
## <a name="see-also"></a><span data-ttu-id="01ec3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01ec3-115">See Also</span></span>  
 <span data-ttu-id="01ec3-116">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="01ec3-116">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="01ec3-117">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="01ec3-117">Object and Collection Initializers</span></span>](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

