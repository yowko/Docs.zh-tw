---
title: -nostdlib (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: cf87d8d2ac4531142288a8637f7fbeb9139382ea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545825"
---
# <a name="-nostdlib-c-compiler-options"></a><span data-ttu-id="57eb9-102">-nostdlib (C# 編譯器選項)</span><span class="sxs-lookup"><span data-stu-id="57eb9-102">-nostdlib (C# Compiler Options)</span></span>

<span data-ttu-id="57eb9-103">**-nostdlib** 會導致無法匯入 mscorlib.dll，而此檔案定義整個系統命名空間。</span><span class="sxs-lookup"><span data-stu-id="57eb9-103">**-nostdlib** prevents the import of mscorlib.dll, which defines the entire System namespace.</span></span>

## <a name="syntax"></a><span data-ttu-id="57eb9-104">語法</span><span class="sxs-lookup"><span data-stu-id="57eb9-104">Syntax</span></span>

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a><span data-ttu-id="57eb9-105">備註</span><span class="sxs-lookup"><span data-stu-id="57eb9-105">Remarks</span></span>

<span data-ttu-id="57eb9-106">如果您想要定義或建立自己的系統命名空間和物件，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="57eb9-106">Use this option if you want to define or create your own System namespace and objects.</span></span>

<span data-ttu-id="57eb9-107">若您沒有指定 **-nostdlib**，mscorlib.dll 會匯入您的程式中 (與指定 **-nostdlib-** 相同)。</span><span class="sxs-lookup"><span data-stu-id="57eb9-107">If you do not specify **-nostdlib**, mscorlib.dll is imported into your program (same as specifying **-nostdlib-**).</span></span> <span data-ttu-id="57eb9-108">指定 **-nostdlib** 等同於指定 **-nostdlib+**。</span><span class="sxs-lookup"><span data-stu-id="57eb9-108">Specifying **-nostdlib** is the same as specifying **-nostdlib+**.</span></span>

### <a name="to-set-this-compiler-option-in-visual-studio"></a><span data-ttu-id="57eb9-109">在 Visual Studio 中設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="57eb9-109">To set this compiler option in Visual Studio</span></span>

> [!NOTE]
> <span data-ttu-id="57eb9-110">下列指示僅適用於 Visual Studio 2015 (及更早版本)。</span><span class="sxs-lookup"><span data-stu-id="57eb9-110">The following instructions apply to Visual Studio 2015 (and earlier versions) only.</span></span> <span data-ttu-id="57eb9-111">[不要參考 mscorlib.dl] 建置屬性在 Visual Studio 2017 中不存在。</span><span class="sxs-lookup"><span data-stu-id="57eb9-111">The **Do not reference mscorlib.dll** build property doesn't exist in Visual Studio 2017.</span></span>

1. <span data-ttu-id="57eb9-112">開啟專案的 [屬性]  頁面。</span><span class="sxs-lookup"><span data-stu-id="57eb9-112">Open the **Properties** page for the project.</span></span>

2. <span data-ttu-id="57eb9-113">按一下 [建置]  屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="57eb9-113">Click the **Build** properties page.</span></span>

3. <span data-ttu-id="57eb9-114">按一下 [ **進階** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="57eb9-114">Click the **Advanced** button.</span></span>

4. <span data-ttu-id="57eb9-115">修改 [不要參考 mscorlib.dll]  屬性。</span><span class="sxs-lookup"><span data-stu-id="57eb9-115">Modify the **Do not reference mscorlib.dll** property.</span></span>

### <a name="to-set-this-compiler-option-programmatically"></a><span data-ttu-id="57eb9-116">若要以程式方式設定這個編譯器選項</span><span class="sxs-lookup"><span data-stu-id="57eb9-116">To set this compiler option programmatically</span></span>

<span data-ttu-id="57eb9-117">如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>。</span><span class="sxs-lookup"><span data-stu-id="57eb9-117">For information on how to set this compiler option programmatically, see <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.</span></span>

## <a name="see-also"></a><span data-ttu-id="57eb9-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57eb9-118">See also</span></span>

- [<span data-ttu-id="57eb9-119">C# 編譯器選項</span><span class="sxs-lookup"><span data-stu-id="57eb9-119">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)
