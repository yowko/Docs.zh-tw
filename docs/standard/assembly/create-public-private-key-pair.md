---
title: 如何：建立公開/私密金鑰組
description: 瞭解如何建立公開/私用密碼編譯金鑰組，以在編譯期間用來建立強式名稱的元件。
ms.date: 08/20/2019
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 675871170e7fd4171f0fe09b04d1dbb8906beda4
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378556"
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="d6b14-103">如何：建立公開/私密金鑰組</span><span class="sxs-lookup"><span data-stu-id="d6b14-103">How to: Create a public-private key pair</span></span>

<span data-ttu-id="d6b14-104">若要使用強式名稱簽署組件，您必須擁有公開/私密金鑰組。</span><span class="sxs-lookup"><span data-stu-id="d6b14-104">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="d6b14-105">這個公用和私密的密碼編譯金鑰組將在編譯期間用來建立強式名稱的組件。</span><span class="sxs-lookup"><span data-stu-id="d6b14-105">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="d6b14-106">您可以使用[強式名稱工具 (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) 來建立金鑰組。</span><span class="sxs-lookup"><span data-stu-id="d6b14-106">You can create a key pair using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="d6b14-107">金鑰組檔案的副檔名通常為 *.snk* 。</span><span class="sxs-lookup"><span data-stu-id="d6b14-107">Key pair files usually have an *.snk* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="d6b14-108">在 Visual Studio 中，c # 和 Visual Basic 專案屬性頁包含 [**簽署**] 索引標籤，可讓您選取現有的金鑰檔或產生新的金鑰檔，而不需要使用*sn.exe*。</span><span class="sxs-lookup"><span data-stu-id="d6b14-108">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using *Sn.exe*.</span></span> <span data-ttu-id="d6b14-109">在 Visual C++ 中，您可以在 [屬性頁]\*\*\*\* 視窗的 [組態屬性]\*\*\*\* 區段之 [連結器]\*\*\*\* 區段的 [進階]\*\*\*\* 屬性頁中，指定現有金鑰檔的位置。</span><span class="sxs-lookup"><span data-stu-id="d6b14-109">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="d6b14-110"><xref:System.Reflection.AssemblyKeyFileAttribute>從 Visual Studio 2005 開始，使用屬性來識別金鑰檔案組已過時。</span><span class="sxs-lookup"><span data-stu-id="d6b14-110">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs was made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="create-a-key-pair"></a><span data-ttu-id="d6b14-111">建立金鑰組</span><span class="sxs-lookup"><span data-stu-id="d6b14-111">Create a key pair</span></span>

<span data-ttu-id="d6b14-112">若要建立金鑰組，請在命令提示字元中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="d6b14-112">To create a key pair, at a command prompt, type the following command:</span></span>

<span data-ttu-id="d6b14-113">**sn –k** \<*file name*></span><span class="sxs-lookup"><span data-stu-id="d6b14-113">**sn –k** \<*file name*></span></span>

<span data-ttu-id="d6b14-114">在這個命令中，*file name* 是含有金鑰組之輸出檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="d6b14-114">In this command, *file name* is the name of the output file containing the key pair.</span></span>

<span data-ttu-id="d6b14-115">下列範例會建立名為*sgKey*的金鑰組。</span><span class="sxs-lookup"><span data-stu-id="d6b14-115">The following example creates a key pair called *sgKey.snk*.</span></span>

```cmd
sn -k sgKey.snk
```

<span data-ttu-id="d6b14-116">如果您想要延遲簽署組件，而且您控制了整個金鑰組 (這大致是發生在測試案例中的情形)，您可以使用下列命令來產生金鑰組，然後從金鑰組解壓縮公開金鑰到個別的檔案中。</span><span class="sxs-lookup"><span data-stu-id="d6b14-116">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="d6b14-117">首先，請建立金鑰組：</span><span class="sxs-lookup"><span data-stu-id="d6b14-117">First, create the key pair:</span></span>

```cmd
sn -k keypair.snk
```

<span data-ttu-id="d6b14-118">接下來，從金鑰組解壓縮公開金鑰，並將公開金鑰複製到個別的檔案中：</span><span class="sxs-lookup"><span data-stu-id="d6b14-118">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```cmd
sn -p keypair.snk public.snk
```

<span data-ttu-id="d6b14-119">建立金鑰組之後，您必須將檔案放到可使用強式名稱簽署工具尋找到的位置。</span><span class="sxs-lookup"><span data-stu-id="d6b14-119">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

<span data-ttu-id="d6b14-120">使用強式名稱簽署組件時，[組件連結器 (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) 會尋找金鑰檔的相關目前目錄和輸出目錄。</span><span class="sxs-lookup"><span data-stu-id="d6b14-120">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="d6b14-121">使用命令列編譯器時，您可以只要將金鑰複製到含有您的程式模組的目前目錄即可。</span><span class="sxs-lookup"><span data-stu-id="d6b14-121">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

<span data-ttu-id="d6b14-122">如果您正在使用舊版的 Visual Studio，而該版本在專案屬性 (Property) 內沒有 [簽署]\*\*\*\* 索引標籤，則建議的金鑰檔位置為專案目錄，並指定如下所示的檔案屬性 (Attribute)：</span><span class="sxs-lookup"><span data-stu-id="d6b14-122">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a><span data-ttu-id="d6b14-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="d6b14-123">See also</span></span>

- [<span data-ttu-id="d6b14-124">建立和使用強式名稱的組件</span><span class="sxs-lookup"><span data-stu-id="d6b14-124">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
