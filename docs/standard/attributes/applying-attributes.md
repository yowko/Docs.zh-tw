---
title: "套用屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- attributes [.NET Framework], applying
ms.assetid: dd7604eb-9fa3-4b60-b2dd-b47739fa3148
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b55684ec30a69bd9773e19420fbe89ca58fd66dd
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="applying-attributes"></a><span data-ttu-id="8986e-102">套用屬性</span><span class="sxs-lookup"><span data-stu-id="8986e-102">Applying Attributes</span></span>
<span data-ttu-id="8986e-103">使用下列流程將屬性套用至程式碼的元素。</span><span class="sxs-lookup"><span data-stu-id="8986e-103">Use the following process to apply an attribute to an element of your code.</span></span>  
  
1.  <span data-ttu-id="8986e-104">定義新屬性，或從 .NET Framework 匯入屬性的命名空間以使用現有的屬性。</span><span class="sxs-lookup"><span data-stu-id="8986e-104">Define a new attribute or use an existing attribute by importing its namespace from the .NET Framework.</span></span>  
  
2.  <span data-ttu-id="8986e-105">將屬性放在緊接於程式碼元素前面，以套用屬性。</span><span class="sxs-lookup"><span data-stu-id="8986e-105">Apply the attribute to the code element by placing it immediately before the element.</span></span>  
  
     <span data-ttu-id="8986e-106">每個語言有其自己的屬性語法。</span><span class="sxs-lookup"><span data-stu-id="8986e-106">Each language has its own attribute syntax.</span></span> <span data-ttu-id="8986e-107">在 C++ 和 C# 中，屬性以方括弧括住，而且與元素之間以空白字元隔開，其中可包含分行符號。</span><span class="sxs-lookup"><span data-stu-id="8986e-107">In C++ and C#, the attribute is surrounded by square brackets and separated from the element by white space, which can include a line break.</span></span> <span data-ttu-id="8986e-108">在 Visual Basic 中，屬性以角括弧括住，而且必須在相同的邏輯行。如果想要分行符號，可以使用行接續字元。</span><span class="sxs-lookup"><span data-stu-id="8986e-108">In Visual Basic, the attribute is surrounded by angle brackets and must be on the same logical line; the line continuation character can be used if a line break is desired.</span></span>
  
3.  <span data-ttu-id="8986e-109">指定屬性的位置參數和具名參數。</span><span class="sxs-lookup"><span data-stu-id="8986e-109">Specify positional parameters and named parameters for the attribute.</span></span>  
  
     <span data-ttu-id="8986e-110">位置參數是必要的，而且必須位於任何具名參數前面。它們對應至屬性的其中一個建構函式的參數。</span><span class="sxs-lookup"><span data-stu-id="8986e-110">Positional parameters are required and must come before any named parameters; they correspond to the parameters of one of the attribute's constructors.</span></span> <span data-ttu-id="8986e-111">具名參數是選擇性，對應至屬性的讀寫屬性。</span><span class="sxs-lookup"><span data-stu-id="8986e-111">Named parameters are optional and correspond to read/write properties of the attribute.</span></span> <span data-ttu-id="8986e-112">在 C++ 和 C# 中，指定每一個選擇性參數的 `name`=`value`，其中 `name` 是屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="8986e-112">In C++, and C#, specify `name`=`value` for each optional parameter, where `name` is the name of the property.</span></span> <span data-ttu-id="8986e-113">在 Visual Basi 中，指定 `name`:=`value`。</span><span class="sxs-lookup"><span data-stu-id="8986e-113">In Visual Basic, specify `name`:=`value`.</span></span>  
  
 <span data-ttu-id="8986e-114">當您編譯程式碼時，屬性會發出至中繼資料，並透過執行階段反映服務，提供給通用語言執行平台及任何自訂工具或應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="8986e-114">The attribute is emitted into metadata when you compile your code and is available to the common language runtime and any custom tool or application through the runtime reflection services.</span></span>  
  
 <span data-ttu-id="8986e-115">依照慣例，所有屬性名稱的結尾都是 Attribute。</span><span class="sxs-lookup"><span data-stu-id="8986e-115">By convention, all attribute names end with Attribute.</span></span> <span data-ttu-id="8986e-116">不過，有幾種以 Visual Basic 和 C# 等執行階段為目標的語言，並不需要您指定屬性的全名。</span><span class="sxs-lookup"><span data-stu-id="8986e-116">However, several languages that target the runtime, such as Visual Basic and C#, do not require you to specify the full name of an attribute.</span></span> <span data-ttu-id="8986e-117">例如，如果您想要初始化 <xref:System.ObsoleteAttribute?displayProperty=nameWithType>，則只需要將其參考為**已淘汰**。</span><span class="sxs-lookup"><span data-stu-id="8986e-117">For example, if you want to initialize <xref:System.ObsoleteAttribute?displayProperty=nameWithType>, you only need to reference it as **Obsolete**.</span></span>  
  
## <a name="applying-an-attribute-to-a-method"></a><span data-ttu-id="8986e-118">將屬性套用至方法</span><span class="sxs-lookup"><span data-stu-id="8986e-118">Applying an Attribute to a Method</span></span>  
 <span data-ttu-id="8986e-119">下列程式碼範例示範如何宣告 **System.ObsoleteAttribute**，將程式碼標記為已淘汰。</span><span class="sxs-lookup"><span data-stu-id="8986e-119">The following code example shows how to declare **System.ObsoleteAttribute**, which marks code as obsolete.</span></span> <span data-ttu-id="8986e-120">`"Will be removed in next version"` 字串會傳遞至屬性。</span><span class="sxs-lookup"><span data-stu-id="8986e-120">The string `"Will be removed in next version"` is passed to the attribute.</span></span> <span data-ttu-id="8986e-121">當呼叫這個屬性所描述的程式碼時，屬性會產生編譯器警告來顯示傳遞的字串。</span><span class="sxs-lookup"><span data-stu-id="8986e-121">This attribute causes a compiler warning that displays the passed string when code that the attribute describes is called.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#3)]
 [!code-csharp[Conceptual.Attributes.Usage#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#3)]
 [!code-vb[Conceptual.Attributes.Usage#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#3)]  
  
## <a name="applying-attributes-at-the-assembly-level"></a><span data-ttu-id="8986e-122">在組件層級套用屬性</span><span class="sxs-lookup"><span data-stu-id="8986e-122">Applying Attributes at the Assembly Level</span></span>  
 <span data-ttu-id="8986e-123">如果您想要在組件層級套用屬性，請使用 **assembly** 關鍵字 (在 Visual Basic 中為 `Assembly`)。</span><span class="sxs-lookup"><span data-stu-id="8986e-123">If you want to apply an attribute at the assembly level, use the **assembly** (`Assembly` in Visual Basic) keyword.</span></span> <span data-ttu-id="8986e-124">下列程式碼顯示在組件層級套用的 **AssemblyTitleAttribute**。</span><span class="sxs-lookup"><span data-stu-id="8986e-124">The following code shows the **AssemblyTitleAttribute** applied at the assembly level.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source1.cpp#2)]
 [!code-csharp[Conceptual.Attributes.Usage#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source1.cs#2)]
 [!code-vb[Conceptual.Attributes.Usage#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source1.vb#2)]  
  
 <span data-ttu-id="8986e-125">套用此屬性時，字串 `"My Assembly"` 會放在檔案的中繼資料部分中的組件資訊清單。</span><span class="sxs-lookup"><span data-stu-id="8986e-125">When this attribute is applied, the string `"My Assembly"` is placed in the assembly manifest in the metadata portion of the file.</span></span> <span data-ttu-id="8986e-126">您可以使用 [MSIL 反組譯工具 (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) 或建立自訂程式擷取屬性，以檢視屬性。</span><span class="sxs-lookup"><span data-stu-id="8986e-126">You can view the attribute either by using the [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) or by creating a custom program to retrieve the attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8986e-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="8986e-127">See Also</span></span>  
 [<span data-ttu-id="8986e-128">屬性</span><span class="sxs-lookup"><span data-stu-id="8986e-128">Attributes</span></span>](../../../docs/standard/attributes/index.md)  
 [<span data-ttu-id="8986e-129">擷取儲存於屬性中的資訊</span><span class="sxs-lookup"><span data-stu-id="8986e-129">Retrieving Information Stored in Attributes</span></span>](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)  
 [<span data-ttu-id="8986e-130">概念</span><span class="sxs-lookup"><span data-stu-id="8986e-130">Concepts</span></span>](/cpp/windows/attributed-programming-concepts)  
 [<span data-ttu-id="8986e-131">屬性</span><span class="sxs-lookup"><span data-stu-id="8986e-131">Attributes</span></span>](http://msdn.microsoft.com/library/ae334cee-d96c-4243-a5e3-06dd7fcaf205)
