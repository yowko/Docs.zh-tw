---
title: 組件內容
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- assemblies [.NET Framework], single-file
- single-file assemblies
- multifile assemblies
ms.assetid: 28116714-da77-45f7-826d-fa035d121948
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2be1aad4d222917364a57abc93b414af40b1e9ae
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675649"
---
# <a name="assembly-contents"></a><span data-ttu-id="53b84-102">組件內容</span><span class="sxs-lookup"><span data-stu-id="53b84-102">Assembly Contents</span></span>
<span data-ttu-id="53b84-103">一般而言，靜態組件可包含四個項目：</span><span class="sxs-lookup"><span data-stu-id="53b84-103">In general, a static assembly can consist of four elements:</span></span>  
  
-   <span data-ttu-id="53b84-104">[組件資訊清單](../../../docs/framework/app-domains/assembly-manifest.md)，其中含有組件中繼資料。</span><span class="sxs-lookup"><span data-stu-id="53b84-104">The [assembly manifest](../../../docs/framework/app-domains/assembly-manifest.md), which contains assembly metadata.</span></span>  
  
-   <span data-ttu-id="53b84-105">型別中繼資料</span><span class="sxs-lookup"><span data-stu-id="53b84-105">Type metadata.</span></span>  
  
-   <span data-ttu-id="53b84-106">會實作型別的 Microsoft Intermediate Language (MSIL) 程式碼</span><span class="sxs-lookup"><span data-stu-id="53b84-106">Microsoft intermediate language (MSIL) code that implements the types.</span></span>  
  
-   <span data-ttu-id="53b84-107">資源集合</span><span class="sxs-lookup"><span data-stu-id="53b84-107">A set of resources.</span></span>  
  
 <span data-ttu-id="53b84-108">只有組件資訊清單是必要項，不過型別或資源兩者必須有一項要用來賦予組件任何有意義的功能。</span><span class="sxs-lookup"><span data-stu-id="53b84-108">Only the assembly manifest is required, but either types or resources are needed to give the assembly any meaningful functionality.</span></span>  
  
 <span data-ttu-id="53b84-109">有幾種方式可以將這些項目群組在組件中。</span><span class="sxs-lookup"><span data-stu-id="53b84-109">There are several ways to group these elements in an assembly.</span></span> <span data-ttu-id="53b84-110">您可以將所有項目群組在一個如下所示的實際檔案中。</span><span class="sxs-lookup"><span data-stu-id="53b84-110">You can group all elements in a single physical file, which is shown in the following illustration.</span></span>  
  
 ![顯示稱為 MyAssembly.dll 之單一檔案組件的圖表。](./media/assembly-contents/single-file-assembly.gif)  
  
 <span data-ttu-id="53b84-112">或者，可以將組件的項目包含在幾個檔案中。</span><span class="sxs-lookup"><span data-stu-id="53b84-112">Alternatively, the elements of an assembly can be contained in several files.</span></span> <span data-ttu-id="53b84-113">這些檔案可以是應用程式所需要的已編譯程式碼模組 (.netmodule)、資源 (例如 .bmp 或 .jpg 檔案) 或是其他檔案。</span><span class="sxs-lookup"><span data-stu-id="53b84-113">These files can be modules of compiled code (.netmodule), resources (such as .bmp or .jpg files), or other files required by the application.</span></span> <span data-ttu-id="53b84-114">如果您希望結合以不同語言所撰寫之模組，並且藉由將不常使用的型別放在需要時才會下載的模組中，以最佳化應用程式的下載，那麼請建立多檔案 (Multifile) 組件。</span><span class="sxs-lookup"><span data-stu-id="53b84-114">Create a multifile assembly when you want to combine modules written in different languages and to optimize downloading an application by putting seldom used types in a module that is downloaded only when needed.</span></span>  
  
 <span data-ttu-id="53b84-115">在下圖中，假想應用程式的開發人員選擇將某些公用程式的程式碼分隔在不同的模組中，並且將大型的資源檔 (在這裡為 .bmp 影像) 存放在原始檔案中。</span><span class="sxs-lookup"><span data-stu-id="53b84-115">In the following illustration, the developer of a hypothetical application has chosen to separate some utility code into a different module and to keep a large resource file (in this case a .bmp image) in its original file.</span></span> <span data-ttu-id="53b84-116">.NET Framework 是在要參考某個檔案的時候才下載它；將不常參考的程式碼保存在應用程式以外的單獨檔案中，可以最佳化程式碼的下載。</span><span class="sxs-lookup"><span data-stu-id="53b84-116">The .NET Framework downloads a file only when it is referenced; keeping infrequently referenced code in a separate file from the application optimizes code download.</span></span>  
  
 ![顯示多檔案組件的圖表。](./media/assembly-contents/multifile-assembly-diagram.gif) 
  
> [!NOTE]
>  <span data-ttu-id="53b84-118">構成多檔案組件的檔案沒有與檔案系統實際連結。</span><span class="sxs-lookup"><span data-stu-id="53b84-118">The files that make up a multifile assembly are not physically linked by the file system.</span></span> <span data-ttu-id="53b84-119">而是透過組件資訊清單連結，而且 Common Language Runtime 會將它們當做一個單位來管理。</span><span class="sxs-lookup"><span data-stu-id="53b84-119">Rather, they are linked through the assembly manifest and the common language runtime manages them as a unit.</span></span>  
  
 <span data-ttu-id="53b84-120">在這個圖中，這三個檔案都屬於一個組件，如同 MyAssembly.dll 中所含組件資訊清單中的描述。</span><span class="sxs-lookup"><span data-stu-id="53b84-120">In this illustration, all three files belong to an assembly, as described in the assembly manifest contained in MyAssembly.dll.</span></span> <span data-ttu-id="53b84-121">對於檔案系統而言，它們是三個不同的檔案。</span><span class="sxs-lookup"><span data-stu-id="53b84-121">To the file system, they are three separate files.</span></span> <span data-ttu-id="53b84-122">請注意，Util.netmodule 這個檔案會編譯為模組，這是因為它並不包含組件資訊。</span><span class="sxs-lookup"><span data-stu-id="53b84-122">Note that the file Util.netmodule was compiled as a module because it contains no assembly information.</span></span> <span data-ttu-id="53b84-123">建立這個組件時，已將組件資訊清單加入至 MyAssembly.dll 中，指出它與 Util.netmodule 和 Graphic.bmp 的關聯性。</span><span class="sxs-lookup"><span data-stu-id="53b84-123">When the assembly was created, the assembly manifest was added to MyAssembly.dll, indicating its relationship with Util.netmodule and Graphic.bmp.</span></span>  
  
 <span data-ttu-id="53b84-124">目前在設計原始程式碼時，您必須明確決定要如何將應用程式的功能分割在一個或多個檔案中。</span><span class="sxs-lookup"><span data-stu-id="53b84-124">As you currently design your source code, you make explicit decisions about how to partition the functionality of your application into one or more files.</span></span> <span data-ttu-id="53b84-125">在設計 .NET Framework 程式碼時，您也必須做出如何將功能分割為一個或多個組件的類似決定。</span><span class="sxs-lookup"><span data-stu-id="53b84-125">When designing .NET Framework code, you will make similar decisions about how to partition the functionality into one or more assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53b84-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53b84-126">See also</span></span>
- [<span data-ttu-id="53b84-127">Common Language Runtime 中的組件</span><span class="sxs-lookup"><span data-stu-id="53b84-127">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
- [<span data-ttu-id="53b84-128">組件資訊清單</span><span class="sxs-lookup"><span data-stu-id="53b84-128">Assembly Manifest</span></span>](../../../docs/framework/app-domains/assembly-manifest.md)
- [<span data-ttu-id="53b84-129">組件安全性考量</span><span class="sxs-lookup"><span data-stu-id="53b84-129">Assembly Security Considerations</span></span>](../../../docs/framework/app-domains/assembly-security-considerations.md)
