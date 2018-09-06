---
title: 型別提供者安全性
description: '了解 F #，包括如何變更型別提供者的信任設定中的型別提供者安全性。'
ms.date: 05/16/2016
ms.openlocfilehash: 26f95ad3950b37a668c497f293b9941ed13a18c7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43861903"
---
# <a name="type-provider-security"></a><span data-ttu-id="1573b-103">型別提供者安全性</span><span class="sxs-lookup"><span data-stu-id="1573b-103">Type Provider Security</span></span>

<span data-ttu-id="1573b-104">型別提供者是組件 (Dll) 由您的 F # 專案或指令碼參考包含連接至外部資料來源，並呈現此類型資訊至 F # 類型環境的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1573b-104">Type providers are assemblies (DLLs) referenced by your F# project or script that contain code to connect to external data sources and surface this type information to the F# type environment.</span></span> <span data-ttu-id="1573b-105">一般而言，當您編譯和接著執行程式碼 （或指令碼時，將程式碼傳送至 F # 互動） 時，是只執行參考組件中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1573b-105">Typically, code in referenced assemblies is only run when you compile and then execute the code (or in the case of a script, send the code to F# Interactive).</span></span> <span data-ttu-id="1573b-106">不過，型別提供者組件會執行在 Visual Studio 中，當程式碼只是已在編輯器中瀏覽。</span><span class="sxs-lookup"><span data-stu-id="1573b-106">However, a type provider assembly will run inside Visual Studio when the code is merely browsed in the editor.</span></span> <span data-ttu-id="1573b-107">這是因為型別提供者需要執行額外的資訊，加入編輯器，例如 快速諮詢工具提示，IntelliSense 完成等等。</span><span class="sxs-lookup"><span data-stu-id="1573b-107">This happens because type providers need to run to add extra information to the editor, such as Quick Info tooltips, IntelliSense completions, and so on.</span></span> <span data-ttu-id="1573b-108">如此一來，有一些額外的安全性考量的型別提供者組件，因為它們會自動在 Visual Studio 處理序內執行。</span><span class="sxs-lookup"><span data-stu-id="1573b-108">As a result, there are extra security considerations for type provider assemblies, since they run automatically inside the Visual Studio process.</span></span>

## <a name="security-warning-dialog"></a><span data-ttu-id="1573b-109">安全性警告對話方塊</span><span class="sxs-lookup"><span data-stu-id="1573b-109">Security Warning Dialog</span></span>

<span data-ttu-id="1573b-110">當第一次使用特定的型別提供者組件，Visual Studio 會顯示警告型別提供者是執行 [安全性] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="1573b-110">When using a particular type provider assembly for the first time, Visual Studio displays a security dialog that warns you that the type provider is about to run.</span></span> <span data-ttu-id="1573b-111">Visual Studio 會載入型別提供者之前，它可讓您決定您是否信任此特定的提供者的機會。</span><span class="sxs-lookup"><span data-stu-id="1573b-111">Before Visual Studio loads the type provider, it gives you the opportunity to decide if you trust this particular provider.</span></span> <span data-ttu-id="1573b-112">如果您信任來源的型別提供者，然後選取 「 我信任此型別提供者 」。</span><span class="sxs-lookup"><span data-stu-id="1573b-112">If you trust the source of the type provider, then select "I trust this type provider."</span></span> <span data-ttu-id="1573b-113">如果您不信任來源的型別提供者，然後選取 我不信任此型別提供者。 」</span><span class="sxs-lookup"><span data-stu-id="1573b-113">If you do not trust the source of the type provider, then select "I do not trust this type provider."</span></span> <span data-ttu-id="1573b-114">信任的提供者，讓它能夠在 Visual Studio 內執行，並提供 IntelliSense 及建置功能。</span><span class="sxs-lookup"><span data-stu-id="1573b-114">Trusting the provider enables it to run inside Visual Studio and provide IntelliSense and build features.</span></span> <span data-ttu-id="1573b-115">但是，如果惡意型別提供者本身，執行其程式碼可能會危害您的電腦。</span><span class="sxs-lookup"><span data-stu-id="1573b-115">But if the type provider itself is malicious, running its code could compromise your machine.</span></span>

<span data-ttu-id="1573b-116">如果您的專案會包含參考型別提供者，您選擇在對話方塊中不信任的程式碼，然後在編譯時期，編譯器會報告錯誤，指出型別提供者不受信任。</span><span class="sxs-lookup"><span data-stu-id="1573b-116">If your project contains code that references type providers that you chose in the dialog not to trust, then at compile time, the compiler will report an error that indicates that the type provider is untrusted.</span></span> <span data-ttu-id="1573b-117">相依於不受信任的型別提供者的任何型別會以紅色波浪線表示。</span><span class="sxs-lookup"><span data-stu-id="1573b-117">Any types that are dependent on the untrusted type provider are indicated by red squiggles.</span></span> <span data-ttu-id="1573b-118">它可以安全地瀏覽程式碼編輯器中。</span><span class="sxs-lookup"><span data-stu-id="1573b-118">It is safe to browse the code in the editor.</span></span>

<span data-ttu-id="1573b-119">如果您決定要變更直接在 Visual Studio 中的信任設定，請執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="1573b-119">If you decide to change the trust setting directly in Visual Studio, perform the following steps.</span></span>

### <a name="to-change-the-trust-settings-for-type-providers"></a><span data-ttu-id="1573b-120">若要變更型別提供者信任設定</span><span class="sxs-lookup"><span data-stu-id="1573b-120">To change the trust settings for type providers</span></span>

1. <span data-ttu-id="1573b-121">在上`Tools`功能表上，選取`Options`，然後展開`F# Tools`節點。</span><span class="sxs-lookup"><span data-stu-id="1573b-121">On the `Tools` menu, select `Options`, and expand the `F# Tools` node.</span></span>

2. <span data-ttu-id="1573b-122">選取`Type Providers`，在型別提供者清單中，型別提供者信任時，請選取此核取方塊並清除那些您不信任的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="1573b-122">Select `Type Providers`, and in the list of type providers, select the check box for type providers you trust, and clear the check box for those you don't trust.</span></span>

## <a name="see-also"></a><span data-ttu-id="1573b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1573b-123">See also</span></span>

- [<span data-ttu-id="1573b-124">類型提供者</span><span class="sxs-lookup"><span data-stu-id="1573b-124">Type Providers</span></span>](index.md)
