---
title: -errorreport
ms.date: 08/14/2018
helpviewer_keywords:
- -errorreport compiler option [Visual Basic]
- /errorreport compiler option [Visual Basic]
- errorreport compiler option [Visual Basic]
ms.assetid: a7fe83a2-a6d8-460c-8dad-79a8f433f501
ms.openlocfilehash: 5471f0783eee5e2c14cf0f140094d5c292a73756
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50186772"
---
# <a name="-errorreport"></a><span data-ttu-id="862a8-102">-errorreport</span><span class="sxs-lookup"><span data-stu-id="862a8-102">-errorreport</span></span>

<span data-ttu-id="862a8-103">指定 Visual Basic 編譯器報告編譯器內部錯誤的方式。</span><span class="sxs-lookup"><span data-stu-id="862a8-103">Specifies how the Visual Basic compiler should report internal compiler errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="862a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="862a8-104">Syntax</span></span>

```
-errorreport:{ prompt | queue | send | none }
```

## <a name="remarks"></a><span data-ttu-id="862a8-105">備註</span><span class="sxs-lookup"><span data-stu-id="862a8-105">Remarks</span></span>

<span data-ttu-id="862a8-106">此選項會提供便利的方式來將 Visual Basic 編譯器內部錯誤 (ICE) 回報到 Microsoft 的 Visual Basic 小組。</span><span class="sxs-lookup"><span data-stu-id="862a8-106">This option provides a convenient way to report a Visual Basic internal compiler error (ICE) to the Visual Basic team at Microsoft.</span></span> <span data-ttu-id="862a8-107">根據預設，編譯器會將任何資訊傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="862a8-107">By default, the compiler sends no information to Microsoft.</span></span> <span data-ttu-id="862a8-108">不過，如果您真的遇到編譯器內部錯誤，此選項可讓您向 Microsoft 回報錯誤。</span><span class="sxs-lookup"><span data-stu-id="862a8-108">However, if you do encounter an internal compiler error, this option allows you to report the error to Microsoft.</span></span> <span data-ttu-id="862a8-109">這項資訊可協助 Microsoft 工程師找出原因，而且可能有助於改善下一版的 Visual Basic。</span><span class="sxs-lookup"><span data-stu-id="862a8-109">That information will help Microsoft engineers identify the cause and may help improve the next release of Visual Basic.</span></span>

<span data-ttu-id="862a8-110">傳送報表的使用者的能力取決於電腦和使用者原則權限。</span><span class="sxs-lookup"><span data-stu-id="862a8-110">A user's ability to send reports depends on machine and user policy permissions.</span></span>

<span data-ttu-id="862a8-111">下表摘要說明的效果`-errorreport`選項。</span><span class="sxs-lookup"><span data-stu-id="862a8-111">The following table summarizes the effect of the `-errorreport` option.</span></span>

|<span data-ttu-id="862a8-112">選項</span><span class="sxs-lookup"><span data-stu-id="862a8-112">Option</span></span>|<span data-ttu-id="862a8-113">行為</span><span class="sxs-lookup"><span data-stu-id="862a8-113">Behavior</span></span>|
|---|---|
|`prompt`|<span data-ttu-id="862a8-114">發生編譯器內部錯誤時，對話方塊隨即出現，您可以檢視編譯器所收集的確切資料。</span><span class="sxs-lookup"><span data-stu-id="862a8-114">If an internal compiler error occurs, a dialog box comes up so that you can view the exact data that the compiler collected.</span></span> <span data-ttu-id="862a8-115">您可以判斷是否有任何錯誤報表中的機密資訊，並決定是否要將它傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="862a8-115">You can determine if there is any sensitive information in the error report and make a decision on whether to send it to Microsoft.</span></span> <span data-ttu-id="862a8-116">如果您決定要傳送，而且電腦和使用者的原則設定允許，編譯器會將資料傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="862a8-116">If you decide to send it, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span>|
|`queue`|<span data-ttu-id="862a8-117">佇列錯誤報告。</span><span class="sxs-lookup"><span data-stu-id="862a8-117">Queues the error report.</span></span> <span data-ttu-id="862a8-118">當您登入系統管理員權限時，您可以在上次登入報告任何失敗 （不會提示您傳送錯誤報告的頻率超過每隔三天一次）。</span><span class="sxs-lookup"><span data-stu-id="862a8-118">When you log in with administrator privileges, you can report any failures since the last time you were logged in (you will not be prompted to send reports for failures more than once every three days).</span></span> <span data-ttu-id="862a8-119">這是預設行為時`-errorreport`未指定選項。</span><span class="sxs-lookup"><span data-stu-id="862a8-119">This is the default behavior when the `-errorreport` option is not specified.</span></span>|
|`send`|<span data-ttu-id="862a8-120">如果發生編譯器內部錯誤，而且電腦和使用者的原則設定允許，編譯器會將資料傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="862a8-120">If an internal compiler error occurs, and the machine and user policy settings allow it, the compiler sends the data to Microsoft.</span></span><br /><br /> <span data-ttu-id="862a8-121">選項`-errorreport:send`會嘗試自動將錯誤資訊傳送給 Microsoft，如果已啟用 reporting [Windows 錯誤報告](/windows/desktop/wer/windows-error-reporting)系統設定。</span><span class="sxs-lookup"><span data-stu-id="862a8-121">The option `-errorreport:send` attempts to automatically send error information to Microsoft if reporting is enabled by the [Windows Error Reporting](/windows/desktop/wer/windows-error-reporting) system settings.</span></span> |
|`none`|<span data-ttu-id="862a8-122">發生編譯器內部錯誤時，它將不會收集或傳送給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="862a8-122">If an internal compiler error occurs, it will not be collected or sent to Microsoft.</span></span>|

<span data-ttu-id="862a8-123">編譯器會將傳送資料，包括堆疊時的錯誤，通常包括一些原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="862a8-123">The compiler sends data that includes the stack at the time of the error, which usually includes some source code.</span></span> <span data-ttu-id="862a8-124">如果`-errorreport`搭配[-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)選項，則會傳送整個原始程式檔。</span><span class="sxs-lookup"><span data-stu-id="862a8-124">If `-errorreport` is used with the [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, then the entire source file is sent.</span></span>

<span data-ttu-id="862a8-125">這個選項最適合搭配[/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)選項，因為它可讓 Microsoft 工程師更輕鬆地重現錯誤。</span><span class="sxs-lookup"><span data-stu-id="862a8-125">This option is best used with the [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md) option, because it allows Microsoft engineers to more easily reproduce the error.</span></span>

> [!NOTE]
> <span data-ttu-id="862a8-126">`-errorreport`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。</span><span class="sxs-lookup"><span data-stu-id="862a8-126">The `-errorreport` option is not available from within the Visual Studio development environment; it is available only when compiling from the command line.</span></span>

## <a name="example"></a><span data-ttu-id="862a8-127">範例</span><span class="sxs-lookup"><span data-stu-id="862a8-127">Example</span></span>

<span data-ttu-id="862a8-128">下列程式碼會嘗試編譯`T2.vb`，和如果編譯器發生編譯器內部錯誤，它會提示您傳送錯誤報表給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="862a8-128">The following code attempts to compile `T2.vb`, and if the compiler encounters an internal compiler error, it prompts you to send the error report to Microsoft.</span></span>

```
vbc -errorreport:prompt t2.vb
```

## <a name="see-also"></a><span data-ttu-id="862a8-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="862a8-129">See also</span></span>

- [<span data-ttu-id="862a8-130">Visual Basic 命令列編譯器</span><span class="sxs-lookup"><span data-stu-id="862a8-130">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)
- [<span data-ttu-id="862a8-131">編譯命令列範例</span><span class="sxs-lookup"><span data-stu-id="862a8-131">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [<span data-ttu-id="862a8-132">-bugreport</span><span class="sxs-lookup"><span data-stu-id="862a8-132">-bugreport</span></span>](../../../visual-basic/reference/command-line-compiler/bugreport.md)
