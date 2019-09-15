---
title: 作法：參考強式名稱的元件
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 324cd42a2781202f19e7e1cb5055d571f0c58cf5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973128"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="cbab3-102">HOW TO：參考強式名稱的元件</span><span class="sxs-lookup"><span data-stu-id="cbab3-102">How to: Reference a strong-named assembly</span></span>
<span data-ttu-id="cbab3-103">參考強式名稱組件中類型或資源的程序通常十分簡單。</span><span class="sxs-lookup"><span data-stu-id="cbab3-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="cbab3-104">您可以在編譯時間 (早期繫結) 或執行階段進行參考。</span><span class="sxs-lookup"><span data-stu-id="cbab3-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
<span data-ttu-id="cbab3-105">當您向編譯器指出要編譯的元件明確參考另一個元件時，就會發生編譯時間參考。</span><span class="sxs-lookup"><span data-stu-id="cbab3-105">A compile-time reference occurs when you indicate to the compiler that the assembly to be compiled explicitly references another assembly.</span></span> <span data-ttu-id="cbab3-106">當您使用編譯時間參考時，編譯器會自動取得目標強式名稱組件的公開金鑰，並將它放在所編譯組件的組件參考中。</span><span class="sxs-lookup"><span data-stu-id="cbab3-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>
  
> [!NOTE]
> <span data-ttu-id="cbab3-107">強式名稱的組件只可使用來自其他強式名稱組件的類型。</span><span class="sxs-lookup"><span data-stu-id="cbab3-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="cbab3-108">否則，強式名稱組件的安全性將會受到危害。</span><span class="sxs-lookup"><span data-stu-id="cbab3-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="cbab3-109">建立強式名稱元件的編譯時間參考</span><span class="sxs-lookup"><span data-stu-id="cbab3-109">Make a compile-time reference to a strong-named assembly</span></span>  

<span data-ttu-id="cbab3-110">在命令提示字元中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="cbab3-110">At a command prompt, type the following command:</span></span>  

<span data-ttu-id="cbab3-111">\<*編譯器命令*>  **/reference:** \<組件名稱></span><span class="sxs-lookup"><span data-stu-id="cbab3-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  

<span data-ttu-id="cbab3-112">在這個命令中，「編譯器命令」是您所使用語言的編譯器命令，而「組件名稱」是所參考的強式名稱組件的名稱。</span><span class="sxs-lookup"><span data-stu-id="cbab3-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="cbab3-113">您也可以使用其他編譯器選項，例如 **/t:library** 選項來建立程式庫組件。</span><span class="sxs-lookup"><span data-stu-id="cbab3-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  

<span data-ttu-id="cbab3-114">下列範例會建立名為*myAssembly*的元件，它會從名為*myAssembly.cs*的程式碼模組參考名為*myLibAssembly*的強式名稱元件。</span><span class="sxs-lookup"><span data-stu-id="cbab3-114">The following example creates an assembly called *myAssembly.dll* that references a strong-named assembly called *myLibAssembly.dll* from a code module called *myAssembly.cs*.</span></span>  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="cbab3-115">建立強式名稱元件的執行時間參考</span><span class="sxs-lookup"><span data-stu-id="cbab3-115">Make a run-time reference to a strong-named assembly</span></span>  
  
<span data-ttu-id="cbab3-116">當您對強式名稱元件（例如使用<xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>或<xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>方法）進行執行時間參考時，您必須使用參考之強式名稱元件的顯示名稱。</span><span class="sxs-lookup"><span data-stu-id="cbab3-116">When you make a run-time reference to a strong-named assembly, for example by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method, you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="cbab3-117">顯示名稱的語法如下：</span><span class="sxs-lookup"><span data-stu-id="cbab3-117">The syntax of a display name is as follows:</span></span>  

<span data-ttu-id="cbab3-118">\<組件名稱> **,** \<版本號碼> **,** \<文化特性> **,** \<公開金鑰權杖></span><span class="sxs-lookup"><span data-stu-id="cbab3-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  

<span data-ttu-id="cbab3-119">例如：</span><span class="sxs-lookup"><span data-stu-id="cbab3-119">For example:</span></span>  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
```  

<span data-ttu-id="cbab3-120">在此範例中，`PublicKeyToken` 是公開金鑰權杖的十六進位格式。</span><span class="sxs-lookup"><span data-stu-id="cbab3-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="cbab3-121">如果沒有文化特性值，請使用 `Culture=neutral`。</span><span class="sxs-lookup"><span data-stu-id="cbab3-121">If there is no culture value, use `Culture=neutral`.</span></span>  

<span data-ttu-id="cbab3-122">下列程式碼範例示範如何搭配使用這項資訊與 <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="cbab3-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  

```cpp
Assembly^ myDll =
    Assembly::Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```csharp
Assembly myDll =
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```vb
Dim myDll As Assembly = _
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1")
```

<span data-ttu-id="cbab3-123">您可以使用下列[強式名稱 (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) 命令，列印特定組件之公開金鑰和公開金鑰權杖的十六進位格式：</span><span class="sxs-lookup"><span data-stu-id="cbab3-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  

<span data-ttu-id="cbab3-124">**sn-Tp \<**  *組件* **>**</span><span class="sxs-lookup"><span data-stu-id="cbab3-124">**sn -Tp \<** *assembly* **>**</span></span>  

<span data-ttu-id="cbab3-125">如果您有公開金鑰檔案，則可以改用下列命令 (請注意命令列選項上的大小寫差異)：</span><span class="sxs-lookup"><span data-stu-id="cbab3-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  

<span data-ttu-id="cbab3-126">**sn -tp \<** *公開金鑰檔* **>**</span><span class="sxs-lookup"><span data-stu-id="cbab3-126">**sn -tp \<** *public key file* **>**</span></span>  

## <a name="see-also"></a><span data-ttu-id="cbab3-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cbab3-127">See also</span></span>

- [<span data-ttu-id="cbab3-128">建立和使用強式名稱的元件</span><span class="sxs-lookup"><span data-stu-id="cbab3-128">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
