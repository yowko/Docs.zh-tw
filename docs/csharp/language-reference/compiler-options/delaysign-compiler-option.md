---
title: "-delaysign (C# 編譯器選項) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /delaysign
dev_langs:
- CSharp
helpviewer_keywords:
- -delaysign compiler option [C#]
- delaysign compiler option [C#]
- /delaysign compiler option [C#]
ms.assetid: bcb058eb-2933-4e7f-b356-5c941db4de75
caps.latest.revision: 16
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
ms.openlocfilehash: 2c5970ebfee3b02335f0fff7af0c0c3784851822
ms.contentlocale: zh-tw
ms.lasthandoff: 05/31/2017

---
# <a name="delaysign-c-compiler-options"></a><span data-ttu-id="8e56a-102">/delaysign (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="8e56a-102">/delaysign (C# Compiler Options)</span></span>
<span data-ttu-id="8e56a-103">這個選項可讓編譯器保留輸出檔案中的空間，以便稍後新增數位簽章。</span><span class="sxs-lookup"><span data-stu-id="8e56a-103">This option causes the compiler to reserve space in the output file so that a digital signature can be added later.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e56a-104">語法</span><span class="sxs-lookup"><span data-stu-id="8e56a-104">Syntax</span></span>  
  
```console  
/delaysign[ + | - ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="8e56a-105">引數</span><span class="sxs-lookup"><span data-stu-id="8e56a-105">Arguments</span></span>  
 <span data-ttu-id="8e56a-106">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="8e56a-106">`+` &#124; `-`</span></span>  
 <span data-ttu-id="8e56a-107">如果需要完整簽署的組件，請使用 **/delaysign-**。</span><span class="sxs-lookup"><span data-stu-id="8e56a-107">Use **/delaysign-** if you want a fully signed assembly.</span></span> <span data-ttu-id="8e56a-108">如果只想在組件中放置公開金鑰，請使用 **/delaysign+**。</span><span class="sxs-lookup"><span data-stu-id="8e56a-108">Use **/delaysign+** if you only want to place the public key in the assembly.</span></span> <span data-ttu-id="8e56a-109">預設值為 **/delaysign-**。</span><span class="sxs-lookup"><span data-stu-id="8e56a-109">The default is **/delaysign-**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8e56a-110">備註</span><span class="sxs-lookup"><span data-stu-id="8e56a-110">Remarks</span></span>  
 <span data-ttu-id="8e56a-111">**/delaysign** 選項必須搭配 [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) 或 [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md) 才有作用。</span><span class="sxs-lookup"><span data-stu-id="8e56a-111">The **/delaysign** option has no effect unless used with [/keyfile](../../../csharp/language-reference/compiler-options/keyfile-compiler-option.md) or [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md).</span></span>  
  
 <span data-ttu-id="8e56a-112">當您要求完整簽署的組件時，編譯器會雜湊包含資訊清單 (組件中繼資料) 的檔案，並使用私密金鑰簽署該雜湊。</span><span class="sxs-lookup"><span data-stu-id="8e56a-112">When you request a fully signed assembly, the compiler hashes the file that contains the manifest (assembly metadata) and signs that hash with the private key.</span></span> <span data-ttu-id="8e56a-113">所產生的數位簽章會儲存在包含資訊清單的檔案中。</span><span class="sxs-lookup"><span data-stu-id="8e56a-113">The resulting digital signature is stored in the file that contains the manifest.</span></span> <span data-ttu-id="8e56a-114">當延遲簽署組件時，編譯器不會去計算和儲存簽章，但會保留檔案中的空間，以便稍後再加入簽章。</span><span class="sxs-lookup"><span data-stu-id="8e56a-114">When an assembly is delay signed, the compiler does not compute and store the signature, but reserves space in the file so the signature can be added later.</span></span>  
  
 <span data-ttu-id="8e56a-115">例如，使用 **/delaysign+** 時，可讓測試人員將組件放入全域快取中。</span><span class="sxs-lookup"><span data-stu-id="8e56a-115">For example, using **/delaysign+** allows a tester to put the assembly in the global cache.</span></span> <span data-ttu-id="8e56a-116">測試之後，您可以使用 [Assembly Linker](https://msdn.microsoft.com/library/c405shex) 公用程式將私密金鑰放入組件中，以完整簽署組件。</span><span class="sxs-lookup"><span data-stu-id="8e56a-116">After testing, you can fully sign the assembly by placing the private key in the assembly using the [Assembly Linker](https://msdn.microsoft.com/library/c405shex) utility.</span></span>  
  
 <span data-ttu-id="8e56a-117">如需詳細資訊，請參閱[建立和使用強式名稱的組件](https://msdn.microsoft.com/library/xwb8f617)和[延遲簽署組件](../../../framework/app-domains/delay-sign-assembly.md)。</span><span class="sxs-lookup"><span data-stu-id="8e56a-117">For more information, see [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) and [Delay Signing an Assembly](../../../framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="8e56a-118">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="8e56a-118">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="8e56a-119">開啟專案的 [屬性]  頁面。</span><span class="sxs-lookup"><span data-stu-id="8e56a-119">Open the **Properties** page for the project.</span></span>  
  
2.  <span data-ttu-id="8e56a-120">修改 [僅延遲簽署] 屬性。</span><span class="sxs-lookup"><span data-stu-id="8e56a-120">Modify the **Delay sign only** property.</span></span>  
  
 <span data-ttu-id="8e56a-121">如需如何以程式設計方式設定這個編譯器選項的資訊，請參閱 <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>。</span><span class="sxs-lookup"><span data-stu-id="8e56a-121">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e56a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e56a-122">See Also</span></span>  
 <span data-ttu-id="8e56a-123">[C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md) </span><span class="sxs-lookup"><span data-stu-id="8e56a-123">[C# Compiler Options](../../../csharp/language-reference/compiler-options/index.md) </span></span>  
<span data-ttu-id="8e56a-124"> [NIB 如何：修改專案屬性和組態設定](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)</span><span class="sxs-lookup"><span data-stu-id="8e56a-124"> [NIB How to: Modify Project Properties and Configuration Settings](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)</span></span>
