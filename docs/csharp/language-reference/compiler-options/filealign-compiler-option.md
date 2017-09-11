---
title: "-filealign (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /filealign
dev_langs:
- CSharp
helpviewer_keywords:
- /alignment compiler option [C#]
- filealign compiler option [C#]
- -filealign compiler option [C#]
- /sections compiler option [C#]
- alignment compiler option [C#]
- sections compiler option [C#]
- -sections compiler option [C#]
- /filealign compiler option [C#]
- file sharing [C#]
- -alignment compiler option [C#]
- section alignment [C#]
ms.assetid: 15cf1c98-3798-4ced-9f08-60619308a073
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: bb28bf28c3d8a426322e1c1795941de7e9aa4bf6
ms.openlocfilehash: 0c33434d26c197ab82e6b72addc750a52a01c5ea
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017

---
# <a name="filealign-c-compiler-options"></a><span data-ttu-id="5f574-102">/filealign (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="5f574-102">/filealign (C# Compiler Options)</span></span>
<span data-ttu-id="5f574-103">**/filealign** 選項可讓您指定輸出檔案中的區段大小。</span><span class="sxs-lookup"><span data-stu-id="5f574-103">The **/filealign** option lets you specify the size of sections in your output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f574-104">語法</span><span class="sxs-lookup"><span data-stu-id="5f574-104">Syntax</span></span>  
  
```console  
/filealign:number  
```  
  
## <a name="arguments"></a><span data-ttu-id="5f574-105">引數</span><span class="sxs-lookup"><span data-stu-id="5f574-105">Arguments</span></span>  
 `number`  
 <span data-ttu-id="5f574-106">指定輸出檔案中區段大小的值。</span><span class="sxs-lookup"><span data-stu-id="5f574-106">A value that specifies the size of sections in the output file.</span></span> <span data-ttu-id="5f574-107">有效值為 512、1024、2048、4096 和 8192。</span><span class="sxs-lookup"><span data-stu-id="5f574-107">Valid values are 512, 1024, 2048, 4096, and 8192.</span></span> <span data-ttu-id="5f574-108">這些值是以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="5f574-108">These values are in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f574-109">備註</span><span class="sxs-lookup"><span data-stu-id="5f574-109">Remarks</span></span>  
 <span data-ttu-id="5f574-110">每個區段將會對齊界限，而這個界限就是 **/filealign**值的倍數。</span><span class="sxs-lookup"><span data-stu-id="5f574-110">Each section will be aligned on a boundary that is a multiple of the **/filealign** value.</span></span> <span data-ttu-id="5f574-111">沒有固定預設值。</span><span class="sxs-lookup"><span data-stu-id="5f574-111">There is no fixed default.</span></span> <span data-ttu-id="5f574-112">如果未指定 **/filealign**，Common Language Runtime 會在編譯時期選取一個預設值。</span><span class="sxs-lookup"><span data-stu-id="5f574-112">If **/filealign** is not specified, the common language runtime picks a default at compile time.</span></span>  
  
 <span data-ttu-id="5f574-113">您可以藉由指定區段大小，來影響輸出檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="5f574-113">By specifying the section size, you affect the size of the output file.</span></span> <span data-ttu-id="5f574-114">修改區段大小對執行於較小裝置上的程式而言可能很有用。</span><span class="sxs-lookup"><span data-stu-id="5f574-114">Modifying section size may be useful for programs that will run on smaller devices.</span></span>  
  
 <span data-ttu-id="5f574-115">請使用 [DUMPBIN](https://docs.microsoft.com/cpp/build/reference/dumpbin-options) 來查看輸出檔案中區段的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5f574-115">Use [DUMPBIN](https://docs.microsoft.com/cpp/build/reference/dumpbin-options) to see information about sections in your output file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="5f574-116">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="5f574-116">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="5f574-117">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="5f574-117">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="5f574-118">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="5f574-118">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="5f574-119">按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5f574-119">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="5f574-120">修改 [檔案對齊] 屬性。</span><span class="sxs-lookup"><span data-stu-id="5f574-120">Modify the **File Alignment** property.</span></span>  
  
 <span data-ttu-id="5f574-121">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>。</span><span class="sxs-lookup"><span data-stu-id="5f574-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.FileAlignment%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f574-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f574-122">See Also</span></span>  
 <span data-ttu-id="5f574-123">[C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="5f574-123">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
<span data-ttu-id="5f574-124"> [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)</span><span class="sxs-lookup"><span data-stu-id="5f574-124"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)</span></span>
