---
title: 在 .NET 中建立主控台應用程式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET, creating console applications
- application development [.NET], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
ms.openlocfilehash: b9c38e1311379037695879565b33ade29c6bf632
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687549"
---
# <a name="console-apps-in-net"></a><span data-ttu-id="740e5-102">.NET 中的主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="740e5-102">Console apps in .NET</span></span>

<span data-ttu-id="740e5-103">.NET 應用程式可以使用 <xref:System.Console?displayProperty=nameWithType> 類別，從主控台讀取字元和寫入字元。</span><span class="sxs-lookup"><span data-stu-id="740e5-103">.NET applications can use the <xref:System.Console?displayProperty=nameWithType> class to read characters from and write characters to the console.</span></span> <span data-ttu-id="740e5-104">來自主控台的資料會從標準輸入資料流讀取，要傳送到主控台的資料會寫入至標準輸出資料流，而傳送給主控台的錯誤資料則會寫入至標準錯誤輸出資料流。</span><span class="sxs-lookup"><span data-stu-id="740e5-104">Data from the console is read from the standard input stream, data to the console is written to the standard output stream, and error data to the console is written to the standard error output stream.</span></span> <span data-ttu-id="740e5-105">在應用程式啟動時，這些資料流會自動與主控台產生關聯，並且分別表示為 <xref:System.Console.In%2A>、<xref:System.Console.Out%2A> 和 <xref:System.Console.Error%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="740e5-105">These streams are automatically associated with the console when the application starts and are presented as the <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, and <xref:System.Console.Error%2A> properties, respectively.</span></span>

<span data-ttu-id="740e5-106"><xref:System.Console.In%2A?displayProperty=nameWithType> 屬性的值是一個 <xref:System.IO.TextReader?displayProperty=nameWithType> 物件，而 <xref:System.Console.Out%2A?displayProperty=nameWithType> 和 <xref:System.Console.Error%2A?displayProperty=nameWithType> 屬性的值則為 <xref:System.IO.TextWriter?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="740e5-106">The value of the <xref:System.Console.In%2A?displayProperty=nameWithType> property is a <xref:System.IO.TextReader?displayProperty=nameWithType> object, whereas the values of the <xref:System.Console.Out%2A?displayProperty=nameWithType> and <xref:System.Console.Error%2A?displayProperty=nameWithType> properties are <xref:System.IO.TextWriter?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="740e5-107">您可以使這些屬性與不代表主控台的資料流產生關聯，讓您能夠替輸入或輸出將資料流指向不同位置。</span><span class="sxs-lookup"><span data-stu-id="740e5-107">You can associate these properties with streams that do not represent the console, making it possible for you to point the stream to a different location for input or output.</span></span> <span data-ttu-id="740e5-108">例如，您可以將 <xref:System.Console.Out%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.IO.StreamWriter?displayProperty=nameWithType>，這樣會透過 <xref:System.Console.SetOut%2A?displayProperty=nameWithType> 方法封裝 <xref:System.IO.FileStream?displayProperty=nameWithType>，藉此將輸出重新導向至檔案。</span><span class="sxs-lookup"><span data-stu-id="740e5-108">For example, you can redirect the output to a file by setting the <xref:System.Console.Out%2A?displayProperty=nameWithType> property to a <xref:System.IO.StreamWriter?displayProperty=nameWithType>, which encapsulates a <xref:System.IO.FileStream?displayProperty=nameWithType> by means of the <xref:System.Console.SetOut%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="740e5-109"><xref:System.Console.In%2A?displayProperty=nameWithType> 和 <xref:System.Console.Out%2A?displayProperty=nameWithType> 屬性不需要參考相同資料流。</span><span class="sxs-lookup"><span data-stu-id="740e5-109">The <xref:System.Console.In%2A?displayProperty=nameWithType> and <xref:System.Console.Out%2A?displayProperty=nameWithType> properties do not need to refer to the same stream.</span></span>

> [!NOTE]
> <span data-ttu-id="740e5-110">如需建置主控台應用程式的詳細資訊 (含 C#、Visual Basic 及 C++ 的範例)，請參閱 <xref:System.Console> 類別的文件。</span><span class="sxs-lookup"><span data-stu-id="740e5-110">For more information about building console applications, including examples in C#, Visual Basic, and C++, see the documentation for the <xref:System.Console> class.</span></span>

<span data-ttu-id="740e5-111">如果主控台不存在（例如，在 Windows Forms 應用程式中），則不會顯示寫入標準輸出資料流程的輸出，因為沒有任何可將資訊寫入的主控台。</span><span class="sxs-lookup"><span data-stu-id="740e5-111">If the console does not exist, for example, in a Windows Forms application, output written to the standard output stream will not be visible, because there is no console to write the information to.</span></span> <span data-ttu-id="740e5-112">將資訊寫入不可存取的主控台不會導致引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="740e5-112">Writing information to an inaccessible console does not cause an exception to be raised.</span></span> <span data-ttu-id="740e5-113"> (您隨時都可以將應用程式類型變更為 **主控台應用程式** ，例如，在 Visual Studio) 的專案屬性頁中。</span><span class="sxs-lookup"><span data-stu-id="740e5-113">(You can always change the application type to **Console Application** , for example, in the project property pages in Visual Studio).</span></span>

<span data-ttu-id="740e5-114">**System.Console** 類別具有可以從主控台讀取個別字元或整行的方法。</span><span class="sxs-lookup"><span data-stu-id="740e5-114">The **System.Console** class has methods that can read individual characters or entire lines from the console.</span></span> <span data-ttu-id="740e5-115">其他方法會轉換資料和格式字串，並接著將格式化的字串寫到主控台。</span><span class="sxs-lookup"><span data-stu-id="740e5-115">Other methods convert data and format strings, and then write the formatted strings to the console.</span></span> <span data-ttu-id="740e5-116">如需格式化字串的詳細資訊，請參閱 [格式化類型](base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="740e5-116">For more information on formatting strings, see [Formatting types](base-types/formatting-types.md).</span></span>

> [!TIP]
> <span data-ttu-id="740e5-117">主控台應用程式缺乏預設會啟動的訊息幫浦 (Message Pump)。</span><span class="sxs-lookup"><span data-stu-id="740e5-117">Console applications lack a message pump that starts by default.</span></span> <span data-ttu-id="740e5-118">因此，對 Microsoft Win32 計時器的主控台呼叫可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="740e5-118">Therefore, console calls to Microsoft Win32 timers might fail.</span></span>

## <a name="see-also"></a><span data-ttu-id="740e5-119">請參閱</span><span class="sxs-lookup"><span data-stu-id="740e5-119">See also</span></span>

- <xref:System.Console?displayProperty=nameWithType>
- [<span data-ttu-id="740e5-120">格式化類型</span><span class="sxs-lookup"><span data-stu-id="740e5-120">Formatting Types</span></span>](base-types/formatting-types.md)
