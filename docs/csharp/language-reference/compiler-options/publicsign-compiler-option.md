---
title: -publicsign (C# 編譯器選項)
ms.date: 05/15/2018
f1_keywords:
- /publicsign
helpviewer_keywords:
- -publicsign compiler option [C#]
- publicsign compiler option [C#]
- /publicsign compiler option [C#]
ms.openlocfilehash: 01ce30b9ac5997f56f29dcbbfa43a27738fa5556
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45678955"
---
# <a name="-publicsign-c-compiler-options"></a><span data-ttu-id="26d8e-102">-publicsign (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="26d8e-102">-publicsign (C# Compiler Options)</span></span>

<span data-ttu-id="26d8e-103">此選項會導致編譯器套用公開金鑰，但實際上不會簽署組件。</span><span class="sxs-lookup"><span data-stu-id="26d8e-103">This option causes the compiler to apply a public key but does not actually sign the assembly.</span></span> <span data-ttu-id="26d8e-104">**-publicsign** 選項也會在組件中設定一個位元，以告知執行階段該檔案實際上已經過簽署。</span><span class="sxs-lookup"><span data-stu-id="26d8e-104">The **-publicsign** option also sets a bit in the assembly that tells the runtime that the file is actually signed.</span></span>

## <a name="syntax"></a><span data-ttu-id="26d8e-105">語法</span><span class="sxs-lookup"><span data-stu-id="26d8e-105">Syntax</span></span>

```console
-publicsign
```

## <a name="arguments"></a><span data-ttu-id="26d8e-106">引數</span><span class="sxs-lookup"><span data-stu-id="26d8e-106">Arguments</span></span>

<span data-ttu-id="26d8e-107">無。</span><span class="sxs-lookup"><span data-stu-id="26d8e-107">None.</span></span>

## <a name="remarks"></a><span data-ttu-id="26d8e-108">備註</span><span class="sxs-lookup"><span data-stu-id="26d8e-108">Remarks</span></span>

<span data-ttu-id="26d8e-109">**-publicsign** 選項需要使用 [-keyfile](keyfile-compiler-option.md) 或 [-keycontainer](keycontainer-compiler-option.md)。</span><span class="sxs-lookup"><span data-stu-id="26d8e-109">The **-publicsign** option requires the use of the [-keyfile](keyfile-compiler-option.md) or [-keycontainer](keycontainer-compiler-option.md).</span></span> <span data-ttu-id="26d8e-110">**Keyfile** 或 **keycontainer** 選項會指定公開金鑰。</span><span class="sxs-lookup"><span data-stu-id="26d8e-110">The **keyfile** or **keycontainer** options specify the public key.</span></span>

<span data-ttu-id="26d8e-111">**-publicsign** 和 **-delaysign** 選項是互斥的。</span><span class="sxs-lookup"><span data-stu-id="26d8e-111">The **-publicsign** and **-delaysign** options are mutually exclusive.</span></span>

<span data-ttu-id="26d8e-112">有時稱為「假簽署」或「OSS 簽署」，公開簽署會在輸出組件中包含公開金鑰並設定「已簽署」的旗標，但實際上不會使用私密金鑰來簽署組件。</span><span class="sxs-lookup"><span data-stu-id="26d8e-112">Sometimes called "fake sign" or "OSS sign", public signing includes the public key in an output assembly and sets the "signed" flag, but doesn't actually sign the assembly with a private key.</span></span> <span data-ttu-id="26d8e-113">這對開放原始碼專案非常實用。在這類專案中，人員想要建置可與已發行「完整簽署」組件相容的組件，但該組件無法存取可用來簽署組件的私密金鑰。</span><span class="sxs-lookup"><span data-stu-id="26d8e-113">This is useful for open source projects where people want to build assemblies which are compatible with the released "fully signed" assemblies, but don't have access to the private key used to sign the assemblies.</span></span> <span data-ttu-id="26d8e-114">由於實際上幾乎沒有任何取用者需要檢查組件是否已完整簽署，因此，這些公開建置的組件幾乎適用於每個要使用完整簽署組件的案例。</span><span class="sxs-lookup"><span data-stu-id="26d8e-114">Since almost no consumers actually need to check if the assembly is fully signed, these publicly built assemblies are useable in almost every scenario where the fully signed one would be used.</span></span>

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="26d8e-115">在 Visual Studio 開發環境中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="26d8e-115">To set this compiler option in the Visual Studio development environment</span></span>

1. <span data-ttu-id="26d8e-116">開啟專案的 [屬性]  頁面。</span><span class="sxs-lookup"><span data-stu-id="26d8e-116">Open the **Properties** page for the project.</span></span>
1. <span data-ttu-id="26d8e-117">修改 [僅延遲簽署] 屬性。</span><span class="sxs-lookup"><span data-stu-id="26d8e-117">Modify the **Delay sign only** property.</span></span>

## <a name="see-also"></a><span data-ttu-id="26d8e-118">請參閱</span><span class="sxs-lookup"><span data-stu-id="26d8e-118">See Also</span></span>

- [<span data-ttu-id="26d8e-119">C# 編譯器 -delaysign 選項</span><span class="sxs-lookup"><span data-stu-id="26d8e-119">C# Compiler -delaysign option</span></span>](delaysign-compiler-option.md)  
- [<span data-ttu-id="26d8e-120">C# 編譯器 -keyfile 選項</span><span class="sxs-lookup"><span data-stu-id="26d8e-120">C# Compiler -keyfile option</span></span>](keyfile-compiler-option.md)  
- [<span data-ttu-id="26d8e-121">C# 編譯器 -keycontainer 選項</span><span class="sxs-lookup"><span data-stu-id="26d8e-121">C# Compiler -keycontainer option</span></span>](keycontainer-compiler-option.md)  
- [<span data-ttu-id="26d8e-122">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="26d8e-122">C# Compiler Options</span></span>](index.md)  
- [<span data-ttu-id="26d8e-123">管理專案和方案屬性</span><span class="sxs-lookup"><span data-stu-id="26d8e-123">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
