---
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: 575b337c262fbb36a9e118aa293916c296cc2db3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408558"
---
# <a name="-keycontainer"></a><span data-ttu-id="a81c0-102">-keycontainer</span><span class="sxs-lookup"><span data-stu-id="a81c0-102">-keycontainer</span></span>
<span data-ttu-id="a81c0-103">指定金鑰組的金鑰容器名稱，為組件提供強式名稱。</span><span class="sxs-lookup"><span data-stu-id="a81c0-103">Specifies a key container name for a key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a81c0-104">語法</span><span class="sxs-lookup"><span data-stu-id="a81c0-104">Syntax</span></span>  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a><span data-ttu-id="a81c0-105">引數</span><span class="sxs-lookup"><span data-stu-id="a81c0-105">Arguments</span></span>  
  
|<span data-ttu-id="a81c0-106">詞彙</span><span class="sxs-lookup"><span data-stu-id="a81c0-106">Term</span></span>|<span data-ttu-id="a81c0-107">定義</span><span class="sxs-lookup"><span data-stu-id="a81c0-107">Definition</span></span>|  
|---|---|  
|`container`|<span data-ttu-id="a81c0-108">必要。</span><span class="sxs-lookup"><span data-stu-id="a81c0-108">Required.</span></span> <span data-ttu-id="a81c0-109">包含金鑰的容器檔案。</span><span class="sxs-lookup"><span data-stu-id="a81c0-109">Container file that contains the key.</span></span> <span data-ttu-id="a81c0-110">如果名稱包含空格，請用引號（""）括住檔案名。</span><span class="sxs-lookup"><span data-stu-id="a81c0-110">Enclose the file name in quotation marks ("") if the name contains a space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a81c0-111">備註</span><span class="sxs-lookup"><span data-stu-id="a81c0-111">Remarks</span></span>  
 <span data-ttu-id="a81c0-112">編譯器會藉由將公開金鑰插入組件資訊清單中，並使用私密金鑰簽署最終元件，來建立可共用的元件。</span><span class="sxs-lookup"><span data-stu-id="a81c0-112">The compiler creates the sharable component by inserting a public key into the assembly manifest and by signing the final assembly with the private key.</span></span> <span data-ttu-id="a81c0-113">若要產生金鑰檔，請在命令列中輸入 `sn -k file`。</span><span class="sxs-lookup"><span data-stu-id="a81c0-113">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="a81c0-114">選項會將 `-i` 金鑰組安裝到容器中。</span><span class="sxs-lookup"><span data-stu-id="a81c0-114">The `-i` option installs the key pair into a container.</span></span> <span data-ttu-id="a81c0-115">如需詳細資訊，請參閱[sn.exe （強式名稱工具）](../../../framework/tools/sn-exe-strong-name-tool.md)）。</span><span class="sxs-lookup"><span data-stu-id="a81c0-115">For more information, see [Sn.exe (Strong Name Tool)](../../../framework/tools/sn-exe-strong-name-tool.md)).</span></span>  
  
 <span data-ttu-id="a81c0-116">如果您使用進行編譯 `-target:module` ，則金鑰檔的名稱會保留在模組中，並併入當您使用[-addmodule](addmodule.md)編譯元件時所建立的元件中。</span><span class="sxs-lookup"><span data-stu-id="a81c0-116">If you compile with `-target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [-addmodule](addmodule.md).</span></span>  
  
 <span data-ttu-id="a81c0-117">您也可以在任何 Microsoft 中繼語言 (MSIL) 模組的原始程式碼中，將這個選項指定為自訂屬性 (<xref:System.Reflection.AssemblyKeyNameAttribute>)。</span><span class="sxs-lookup"><span data-stu-id="a81c0-117">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyNameAttribute>) in the source code for any Microsoft intermediate language (MSIL) module.</span></span>  
  
 <span data-ttu-id="a81c0-118">您也可以使用 [-keyfile](keyfile.md) 將加密資訊傳遞給編譯器。</span><span class="sxs-lookup"><span data-stu-id="a81c0-118">You can also pass your encryption information to the compiler with [-keyfile](keyfile.md).</span></span> <span data-ttu-id="a81c0-119">如需部分簽署的組件，請使用 [-delaysign](delaysign.md)。</span><span class="sxs-lookup"><span data-stu-id="a81c0-119">Use [-delaysign](delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="a81c0-120">如需簽署元件的詳細資訊，請參閱[建立和使用強式名稱的元件](../../../standard/assembly/create-use-strong-named.md)。</span><span class="sxs-lookup"><span data-stu-id="a81c0-120">See [Creating and Using Strong-Named Assemblies](../../../standard/assembly/create-use-strong-named.md) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a81c0-121">此 `-keycontainer` 選項無法從 Visual Studio 開發環境中使用; 只有在從命令列進行編譯時，才能使用此選項。</span><span class="sxs-lookup"><span data-stu-id="a81c0-121">The `-keycontainer` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a81c0-122">範例</span><span class="sxs-lookup"><span data-stu-id="a81c0-122">Example</span></span>  
 <span data-ttu-id="a81c0-123">下列程式碼會編譯原始程式檔 `Input.vb` ，並指定金鑰容器。</span><span class="sxs-lookup"><span data-stu-id="a81c0-123">The following code compiles source file `Input.vb` and specifies a key container.</span></span>  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="a81c0-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a81c0-124">See also</span></span>

- [<span data-ttu-id="a81c0-125">.NET 中的組件</span><span class="sxs-lookup"><span data-stu-id="a81c0-125">Assemblies in .NET</span></span>](../../../standard/assembly/index.md)
- [<span data-ttu-id="a81c0-126">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="a81c0-126">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="a81c0-127">-keyfile</span><span class="sxs-lookup"><span data-stu-id="a81c0-127">-keyfile</span></span>](keyfile.md)
- [<span data-ttu-id="a81c0-128">編譯命令列的範例</span><span class="sxs-lookup"><span data-stu-id="a81c0-128">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
