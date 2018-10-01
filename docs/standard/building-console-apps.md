---
title: 在 .NET Framework 中建置主控台應用程式
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- .NET Framework, building console applications
- application development [.NET Framework], console
- console applications
ms.assetid: c21fb997-9f0e-40a5-8741-f73bba376bd8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 979989c3e1f90f3de47473aa1bd8bc5268520e57
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47402457"
---
# <a name="building-console-applications-in-the-net-framework"></a><span data-ttu-id="4f5b8-102">在 .NET Framework 中建置主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="4f5b8-102">Building Console Applications in the .NET Framework</span></span>
<span data-ttu-id="4f5b8-103">.NET Framework 中的應用程式可以使用 <xref:System.Console?displayProperty=nameWithType> 類別從主控台讀取字元，以及將字元寫入主控台。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-103">Applications in the .NET Framework can use the <xref:System.Console?displayProperty=nameWithType> class to read characters from and write characters to the console.</span></span> <span data-ttu-id="4f5b8-104">來自主控台的資料會從標準輸入資料流讀取，要傳送到主控台的資料會寫入至標準輸出資料流，而傳送給主控台的錯誤資料則會寫入至標準錯誤輸出資料流。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-104">Data from the console is read from the standard input stream, data to the console is written to the standard output stream, and error data to the console is written to the standard error output stream.</span></span> <span data-ttu-id="4f5b8-105">在應用程式啟動時，這些資料流會自動與主控台產生關聯，並且分別表示為 <xref:System.Console.In%2A>、<xref:System.Console.Out%2A> 和 <xref:System.Console.Error%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-105">These streams are automatically associated with the console when the application starts and are presented as the <xref:System.Console.In%2A>, <xref:System.Console.Out%2A>, and <xref:System.Console.Error%2A> properties, respectively.</span></span>  
  
 <span data-ttu-id="4f5b8-106"><xref:System.Console.In%2A?displayProperty=nameWithType> 屬性的值是一個 <xref:System.IO.TextReader?displayProperty=nameWithType> 物件，而 <xref:System.Console.Out%2A?displayProperty=nameWithType> 和 <xref:System.Console.Error%2A?displayProperty=nameWithType> 屬性的值則為 <xref:System.IO.TextWriter?displayProperty=nameWithType> 物件。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-106">The value of the <xref:System.Console.In%2A?displayProperty=nameWithType> property is a <xref:System.IO.TextReader?displayProperty=nameWithType> object, whereas the values of the <xref:System.Console.Out%2A?displayProperty=nameWithType> and <xref:System.Console.Error%2A?displayProperty=nameWithType> properties are <xref:System.IO.TextWriter?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="4f5b8-107">您可以使這些屬性與不代表主控台的資料流產生關聯，讓您能夠替輸入或輸出將資料流指向不同位置。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-107">You can associate these properties with streams that do not represent the console, making it possible for you to point the stream to a different location for input or output.</span></span> <span data-ttu-id="4f5b8-108">例如，您可以將 <xref:System.Console.Out%2A?displayProperty=nameWithType> 屬性設定為 <xref:System.IO.StreamWriter?displayProperty=nameWithType>，這樣會透過 <xref:System.Console.SetOut%2A?displayProperty=nameWithType> 方法封裝 <xref:System.IO.FileStream?displayProperty=nameWithType>，藉此將輸出重新導向至檔案。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-108">For example, you can redirect the output to a file by setting the <xref:System.Console.Out%2A?displayProperty=nameWithType> property to a <xref:System.IO.StreamWriter?displayProperty=nameWithType>, which encapsulates a <xref:System.IO.FileStream?displayProperty=nameWithType> by means of the <xref:System.Console.SetOut%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4f5b8-109"><xref:System.Console.In%2A?displayProperty=nameWithType> 和 <xref:System.Console.Out%2A?displayProperty=nameWithType> 屬性不需要參考相同資料流。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-109">The <xref:System.Console.In%2A?displayProperty=nameWithType> and <xref:System.Console.Out%2A?displayProperty=nameWithType> properties do not need to refer to the same stream.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f5b8-110">如需建置主控台應用程式的詳細資訊 (含 C#、Visual Basic 及 C++ 的範例)，請參閱 <xref:System.Console> 類別的文件。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-110">For more information about building console applications, including examples in C#, Visual Basic, and C++, see the documentation for the <xref:System.Console> class.</span></span>  
  
 <span data-ttu-id="4f5b8-111">因為沒有可以將資訊寫入的主控台，所以如果主控台不存在 (例如在 Windows 架構應用程式中) 的話，將看不到寫入標準輸出資料流的輸出。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-111">If the console does not exist, as in a Windows-based application, output written to the standard output stream will not be visible, because there is no console to write the information to.</span></span> <span data-ttu-id="4f5b8-112">將資訊寫入不可存取的主控台不會導致引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-112">Writing information to an inaccessible console does not cause an exception to be raised.</span></span>  
  
 <span data-ttu-id="4f5b8-113">此外，若要在使用 Visual Studio 開發的 Windows 架構應用程式內啟用主控台來讀取和寫入，請開啟專案的 [屬性] 對話方塊，按一下 [應用程式] 索引標籤，然後將 [應用程式類型] 設定為 [主控台應用程式]。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-113">Alternately, to enable the console for reading and writing within a Windows-based application that is developed using Visual Studio, open the project's **Properties** dialog box, click the **Application** tab, and set the **Application type** to **Console Application**.</span></span>  
  
 <span data-ttu-id="4f5b8-114">主控台應用程式缺乏預設會啟動的訊息幫浦 (Message Pump)。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-114">Console applications lack a message pump that starts by default.</span></span> <span data-ttu-id="4f5b8-115">因此，對 Microsoft Win32 計時器的主控台呼叫可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-115">Therefore, console calls to Microsoft Win32 timers might fail.</span></span>  
  
 <span data-ttu-id="4f5b8-116">**System.Console** 類別具有可以從主控台讀取個別字元或整行的方法。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-116">The **System.Console** class has methods that can read individual characters or entire lines from the console.</span></span> <span data-ttu-id="4f5b8-117">其他方法會轉換資料和格式字串，並接著將格式化的字串寫到主控台。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-117">Other methods convert data and format strings, and then write the formatted strings to the console.</span></span> <span data-ttu-id="4f5b8-118">如需格式化字串的詳細資訊，請參閱[格式化類型](../../docs/standard/base-types/formatting-types.md)。</span><span class="sxs-lookup"><span data-stu-id="4f5b8-118">For more information on formatting strings, see [Formatting Types](../../docs/standard/base-types/formatting-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f5b8-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f5b8-119">See also</span></span>

- <xref:System.Console?displayProperty=nameWithType>  
- [<span data-ttu-id="4f5b8-120">格式化類型</span><span class="sxs-lookup"><span data-stu-id="4f5b8-120">Formatting Types</span></span>](../../docs/standard/base-types/formatting-types.md)
