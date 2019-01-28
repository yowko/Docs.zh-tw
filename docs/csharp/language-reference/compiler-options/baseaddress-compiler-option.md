---
title: -baseaddress (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /dllbase
helpviewer_keywords:
- baseaddress compiler option [C#]
- -baseaddress compiler option [C#]
- /baseaddress compiler option [C#]
ms.assetid: ce13c965-dfe4-4433-94f5-63b476e3a608
ms.openlocfilehash: 6ff29a7a204cb8f20f2f67946d5d1ed9c976e7aa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54694570"
---
# <a name="-baseaddress-c-compiler-options"></a><span data-ttu-id="79021-102">-baseaddress (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="79021-102">-baseaddress (C# Compiler Options)</span></span>
<span data-ttu-id="79021-103">**-baseaddress** 選項讓您指定要載入 DLL 的慣用基底位址。</span><span class="sxs-lookup"><span data-stu-id="79021-103">The **-baseaddress** option lets you specify the preferred base address at which to load a DLL.</span></span> <span data-ttu-id="79021-104">如需此選項的使用時機與使用原因之詳細資訊，請參閱 [Larry Osterman 的部落格](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/)。</span><span class="sxs-lookup"><span data-stu-id="79021-104">For more information about when and why to use this option, see [Larry Osterman's WebLog](https://blogs.msdn.microsoft.com/larryosterman/2004/07/06/why-should-i-even-bother-to-use-dlls-in-my-system/).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79021-105">語法</span><span class="sxs-lookup"><span data-stu-id="79021-105">Syntax</span></span>  
  
```console  
-baseaddress:address  
```  
  
## <a name="arguments"></a><span data-ttu-id="79021-106">引數</span><span class="sxs-lookup"><span data-stu-id="79021-106">Arguments</span></span>  
 `address`  
 <span data-ttu-id="79021-107">DLL 的基底位址。</span><span class="sxs-lookup"><span data-stu-id="79021-107">The base address for the DLL.</span></span> <span data-ttu-id="79021-108">這個位址可以指定十進位、十六進位或八進位數字。</span><span class="sxs-lookup"><span data-stu-id="79021-108">This address can be specified as a decimal, hexadecimal, or octal number.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79021-109">備註</span><span class="sxs-lookup"><span data-stu-id="79021-109">Remarks</span></span>  
 <span data-ttu-id="79021-110">DLL 的預設基底位址是由 .NET Framework Common Language Runtime 所設定。</span><span class="sxs-lookup"><span data-stu-id="79021-110">The default base address for a DLL is set by the .NET Framework common language runtime.</span></span>  
  
 <span data-ttu-id="79021-111">請注意，這個位址會去掉低位字。</span><span class="sxs-lookup"><span data-stu-id="79021-111">Be aware that the lower-order word in this address will be rounded.</span></span> <span data-ttu-id="79021-112">例如，如果您指定的是 0x11110001，它會去掉尾數變成 0x11110000。</span><span class="sxs-lookup"><span data-stu-id="79021-112">For example, if you specify 0x11110001, it will be rounded to 0x11110000.</span></span>  
  
 <span data-ttu-id="79021-113">若要完成 DLL 的簽章程序，請使用 SN.EXE 和 -R 選項。</span><span class="sxs-lookup"><span data-stu-id="79021-113">To complete the signing process for a DLL, use SN.EXE with the -R option.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="79021-114">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="79021-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1.  <span data-ttu-id="79021-115">開啟專案的 [屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="79021-115">Open the project's **Properties** page.</span></span>  
  
2.  <span data-ttu-id="79021-116">按一下 [建置] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="79021-116">Click the **Build** property page.</span></span>  
  
3.  <span data-ttu-id="79021-117">按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="79021-117">Click the **Advanced** button.</span></span>  
  
4.  <span data-ttu-id="79021-118">修改 **DLL 基底位址**屬性。</span><span class="sxs-lookup"><span data-stu-id="79021-118">Modify the **DLL Base Address** property.</span></span>  
  
     <span data-ttu-id="79021-119">若要以程式設計方式設定這個編譯器選項，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>。</span><span class="sxs-lookup"><span data-stu-id="79021-119">To set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.BaseAddress%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79021-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="79021-120">See also</span></span>

- <xref:System.Diagnostics.ProcessModule.BaseAddress%2A?displayProperty=nameWithType>
- [<span data-ttu-id="79021-121">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="79021-121">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
- [<span data-ttu-id="79021-122">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="79021-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
