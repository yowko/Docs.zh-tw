---
title: 原生互通性 - .NET
description: 了解如何連接到 .NET 中的原生元件。
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 85a22394c8c59f51f462bc0a2ba6a11265682db3
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54416050"
---
# <a name="native-interoperability"></a><span data-ttu-id="b4741-103">原生互通性</span><span class="sxs-lookup"><span data-stu-id="b4741-103">Native interoperability</span></span>

<span data-ttu-id="b4741-104">下列文章說明在 .NET 中執行「原生互通性」的各種方式。</span><span class="sxs-lookup"><span data-stu-id="b4741-104">The following articles show the various ways of doing "native interoperability" in .NET.</span></span>

<span data-ttu-id="b4741-105">以下為您應呼叫機器碼的幾個原因︰</span><span class="sxs-lookup"><span data-stu-id="b4741-105">There are a few reasons why you'd want to call into native code:</span></span>

* <span data-ttu-id="b4741-106">作業系統隨附大量受控類別庫中所沒有的 API。</span><span class="sxs-lookup"><span data-stu-id="b4741-106">Operating systems come with a large volume of APIs that aren't present in the managed class libraries.</span></span> <span data-ttu-id="b4741-107">此情節的基本範例將會說明存取硬體或作業系統管理功能。</span><span class="sxs-lookup"><span data-stu-id="b4741-107">A prime example for this scenario would be access to hardware or operating system management functions.</span></span>
* <span data-ttu-id="b4741-108">與其他擁有或可產生 C 樣式 ABI (原生 ABI) 的元件通訊，像是透過 [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) 公開的 Java 程式碼，或是任何可產生原生元件的受控語言。</span><span class="sxs-lookup"><span data-stu-id="b4741-108">Communicating with other components that have or can produce C-style ABIs (native ABIs), such as Java code that is exposed via [Java Native Interface (JNI)](https://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
* <span data-ttu-id="b4741-109">在 Windows 上，大部分的已安裝軟體 (例如 Microsoft Office 套件) 會註冊 COM 元件，這些元件代表其程式，且可讓開發人員予以自動化或使用。</span><span class="sxs-lookup"><span data-stu-id="b4741-109">On Windows, most of the software that gets installed, such as the Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="b4741-110">而這也需要原生互通性。</span><span class="sxs-lookup"><span data-stu-id="b4741-110">This also requires native interoperability.</span></span>

<span data-ttu-id="b4741-111">上述清單並未涵蓋所有開發人員會想要，或必須與原生元件互動的可能情況和情節。</span><span class="sxs-lookup"><span data-stu-id="b4741-111">The previous list doesn't cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="b4741-112">舉例來說，.NET 類別庫會使用原生互通性支援來實作其一部分的 API，例如主控台支援和操作、檔案系統存取權及其他項目。</span><span class="sxs-lookup"><span data-stu-id="b4741-112">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="b4741-113">不過請務必注意，您可視需要選擇使用。</span><span class="sxs-lookup"><span data-stu-id="b4741-113">However, it's important to note that there's an option if needed.</span></span>

> [!NOTE]
> <span data-ttu-id="b4741-114">本節中大部分範例會針對 .NET Core 的所有三種支援平台 (Windows、Linux 和 macOS) 來呈現。</span><span class="sxs-lookup"><span data-stu-id="b4741-114">Most of the examples in this section will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="b4741-115">不過，對於一些簡短和說明性的範例，只會顯示一個使用 Windows 檔名和副檔名 (也就是代表程式庫的 "dll") 的範例。</span><span class="sxs-lookup"><span data-stu-id="b4741-115">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="b4741-116">這不表示您無法在 Linux 或 macOS 上使用這些功能，如此呈現只是為了方便起見。</span><span class="sxs-lookup"><span data-stu-id="b4741-116">This doesn't mean that those features aren't available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="see-also"></a><span data-ttu-id="b4741-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4741-117">See also</span></span>

- [<span data-ttu-id="b4741-118">平台叫用 (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="b4741-118">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
- [<span data-ttu-id="b4741-119">類型封送處理</span><span class="sxs-lookup"><span data-stu-id="b4741-119">Type marshalling</span></span>](type-marshalling.md)
