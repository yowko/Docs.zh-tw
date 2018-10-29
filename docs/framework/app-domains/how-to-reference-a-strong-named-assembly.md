---
title: 如何：參考強式名稱簽署組件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18844a9e8eff574d061b044bf88bc7857ce8033e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50182979"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="b332d-102">如何：參考強式名稱簽署組件</span><span class="sxs-lookup"><span data-stu-id="b332d-102">How to: Reference a Strong-Named Assembly</span></span>
<span data-ttu-id="b332d-103">參考強式名稱組件中類型或資源的程序通常十分簡單。</span><span class="sxs-lookup"><span data-stu-id="b332d-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="b332d-104">您可以在編譯時間 (早期繫結) 或執行階段進行參考。</span><span class="sxs-lookup"><span data-stu-id="b332d-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
 <span data-ttu-id="b332d-105">當您對編譯器指出您的組件明確參考另一個組件時，就會發生編譯時間參考。</span><span class="sxs-lookup"><span data-stu-id="b332d-105">A compile-time reference occurs when you indicate to the compiler that your assembly explicitly references another assembly.</span></span> <span data-ttu-id="b332d-106">當您使用編譯時間參考時，編譯器會自動取得目標強式名稱組件的公開金鑰，並將它放在所編譯組件的組件參考中。</span><span class="sxs-lookup"><span data-stu-id="b332d-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b332d-107">強式名稱的組件只可使用來自其他強式名稱組件的類型。</span><span class="sxs-lookup"><span data-stu-id="b332d-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="b332d-108">否則，強式名稱組件的安全性將會受到危害。</span><span class="sxs-lookup"><span data-stu-id="b332d-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="b332d-109">建立強式名稱組件的編譯時間參考</span><span class="sxs-lookup"><span data-stu-id="b332d-109">To make a compile-time reference to a strong-named assembly</span></span>  
  
1.  <span data-ttu-id="b332d-110">在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="b332d-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="b332d-111">\<*編譯器命令*> **/reference:**\<組件名稱></span><span class="sxs-lookup"><span data-stu-id="b332d-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  
  
     <span data-ttu-id="b332d-112">在這個命令中，「編譯器命令」是您所使用語言的編譯器命令，而「組件名稱」是所參考的強式名稱組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="b332d-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="b332d-113">您也可以使用其他編譯器選項，例如 **/t:library** 選項來建立程式庫組件。</span><span class="sxs-lookup"><span data-stu-id="b332d-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  
  
 <span data-ttu-id="b332d-114">下列範例會建立稱為 `myAssembly.dll` 的組件，而此組件從稱為 `myAssembly.cs` 的程式碼模組參考稱為 `myLibAssembly.dll` 的強式名稱組件。</span><span class="sxs-lookup"><span data-stu-id="b332d-114">The following example creates an assembly called `myAssembly.dll` that references a strong-named assembly called `myLibAssembly.dll` from a code module called `myAssembly.cs`.</span></span>  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="b332d-115">建立強式名稱組件的執行階段參考</span><span class="sxs-lookup"><span data-stu-id="b332d-115">To make a run-time reference to a strong-named assembly</span></span>  
  
1.  <span data-ttu-id="b332d-116">當您建立強式名稱組件的執行階段參考時 (例如，使用 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 或 <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> 方法)，必須使用所參考之強式名稱組件的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="b332d-116">When you make a run-time reference to a strong-named assembly (for example, by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method), you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="b332d-117">顯示名稱的語法如下：</span><span class="sxs-lookup"><span data-stu-id="b332d-117">The syntax of a display name is as follows:</span></span>  
  
     <span data-ttu-id="b332d-118">\<組件名稱>**,** \<版本號碼>**,** \<文化特性>**,** \<公開金鑰權杖></span><span class="sxs-lookup"><span data-stu-id="b332d-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  
  
     <span data-ttu-id="b332d-119">例如: </span><span class="sxs-lookup"><span data-stu-id="b332d-119">For example:</span></span>  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     <span data-ttu-id="b332d-120">在此範例中，`PublicKeyToken` 是公開金鑰權杖的十六進位格式。</span><span class="sxs-lookup"><span data-stu-id="b332d-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="b332d-121">如果沒有文化特性值，請使用 `Culture=neutral`。</span><span class="sxs-lookup"><span data-stu-id="b332d-121">If there is no culture value, use `Culture=neutral`.</span></span>  
  
 <span data-ttu-id="b332d-122">下列程式碼範例示範如何搭配使用這項資訊與 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="b332d-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 <span data-ttu-id="b332d-123">您可以使用下列[強式名稱 (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) 命令，列印特定組件之公開金鑰和公開金鑰權杖的十六進位格式：</span><span class="sxs-lookup"><span data-stu-id="b332d-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  
  
 <span data-ttu-id="b332d-124">**sn -Tp \<** 組件**>**</span><span class="sxs-lookup"><span data-stu-id="b332d-124">**sn -Tp \<** *assembly* **>**</span></span>  
  
 <span data-ttu-id="b332d-125">如果您有公開金鑰檔案，則可以改用下列命令 (請注意命令列選項上的大小寫差異)：</span><span class="sxs-lookup"><span data-stu-id="b332d-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  
  
 <span data-ttu-id="b332d-126">**sn -tp \<** *公開金鑰檔* **>**</span><span class="sxs-lookup"><span data-stu-id="b332d-126">**sn -tp \<** *public key file* **>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b332d-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="b332d-127">See Also</span></span>  
- [<span data-ttu-id="b332d-128">建立和使用強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="b332d-128">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
