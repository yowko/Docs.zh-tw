---
title: 作法：將事件資訊寫入文字檔
ms.date: 07/20/2015
helpviewer_keywords:
- event logs [Visual Studio], writing event information
- text files [Visual Basic], writing event information to a text file
- events [Visual Basic], writing event information to a text file
ms.assetid: 9ca7cc03-bf99-4933-9e5e-61ee28e9a6b4
ms.openlocfilehash: 6e83f8450ca7be8a2dcd5ff43eab3dd2ec0d2f1b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410058"
---
# <a name="how-to-write-event-information-to-a-text-file-visual-basic"></a><span data-ttu-id="d48ce-102">如何：將事件資訊寫入至文字檔 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d48ce-102">How to: Write Event Information to a Text File (Visual Basic)</span></span>

<span data-ttu-id="d48ce-103">您可以使用 `My.Application.Log` 和 `My.Log` 物件來記錄應用程式中發生之事件的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d48ce-103">You can use the `My.Application.Log` and `My.Log` objects to log information about events that occur in your application.</span></span> <span data-ttu-id="d48ce-104">這個範例示範如何使用 `My.Application.Log.WriteEntry` 方法將追蹤資訊記錄到記錄檔。</span><span class="sxs-lookup"><span data-stu-id="d48ce-104">This example shows how to use the `My.Application.Log.WriteEntry` method to log tracing information to a log file.</span></span>

### <a name="to-add-and-configure-the-file-log-listener"></a><span data-ttu-id="d48ce-105">新增和設定檔案記錄檔接聽程式</span><span class="sxs-lookup"><span data-stu-id="d48ce-105">To add and configure the file log listener</span></span>

1. <span data-ttu-id="d48ce-106">在 方案總管 中，以滑鼠右鍵按一下 app.config 並選擇 [開啟]。\*\*\*\*\*\*\*\*</span><span class="sxs-lookup"><span data-stu-id="d48ce-106">Right-click app.config in **Solution Explorer** and choose **Open**.</span></span>

     <span data-ttu-id="d48ce-107">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="d48ce-107">\- or -</span></span>

     <span data-ttu-id="d48ce-108">如果沒有 app.config 檔案︰</span><span class="sxs-lookup"><span data-stu-id="d48ce-108">If there is no app.config file:</span></span>

    1. <span data-ttu-id="d48ce-109">在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。</span><span class="sxs-lookup"><span data-stu-id="d48ce-109">On the **Project** menu, choose **Add New Item**.</span></span>

    2. <span data-ttu-id="d48ce-110">在 [加入新項目] \*\*\*\* 對話方塊中，選擇 [應用程式組態檔] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d48ce-110">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>

    3. <span data-ttu-id="d48ce-111">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="d48ce-111">Click **Add**.</span></span>

2. <span data-ttu-id="d48ce-112">在應用程式組態檔中找出 `<listeners>` 區段。</span><span class="sxs-lookup"><span data-stu-id="d48ce-112">Locate the `<listeners>` section in the application configuration file.</span></span>

     <span data-ttu-id="d48ce-113">您會找到名稱屬性為 "DefaultSource" 之 \<listeners> 區段 (位於最上層 \<source> 區段底下 \<system.diagnostics> 區段中) 中的 \<configuration> 區段。</span><span class="sxs-lookup"><span data-stu-id="d48ce-113">You will find the \<listeners> section in the \<source> section with the name attribute "DefaultSource", which is nested under the \<system.diagnostics> section, which is nested under the top-level \<configuration> section.</span></span>

3. <span data-ttu-id="d48ce-114">將此項目加入至該 `<listeners>` 區段︰</span><span class="sxs-lookup"><span data-stu-id="d48ce-114">Add this element to that `<listeners>` section:</span></span>

    ```xml
    <add name="FileLogListener" />
    ```

4. <span data-ttu-id="d48ce-115">找出巢狀於最上層 `<configuration>` 區段中 `<system.diagnostics>` 區段的 `<sharedListeners>` 區段。</span><span class="sxs-lookup"><span data-stu-id="d48ce-115">Locate the `<sharedListeners>` section in the `<system.diagnostics>` section, nested under the top-level `<configuration>` section.</span></span>

5. <span data-ttu-id="d48ce-116">將此項目加入至該 `<sharedListeners>` 區段︰</span><span class="sxs-lookup"><span data-stu-id="d48ce-116">Add this element to that `<sharedListeners>` section:</span></span>

    ```xml
    <add name="FileLogListener"
        type="Microsoft.VisualBasic.Logging.FileLogTraceListener,
              Microsoft.VisualBasic, Version=8.0.0.0, Culture=neutral,
              PublicKeyToken=b03f5f7f11d50a3a"
        initializeData="FileLogListenerWriter"
        location="Custom"
        customlocation="c:\temp\" />
    ```

     <span data-ttu-id="d48ce-117">將 `customlocation` 屬性的值變更為記錄檔目錄。</span><span class="sxs-lookup"><span data-stu-id="d48ce-117">Change the value of the `customlocation` attribute to the log directory.</span></span>

    > [!NOTE]
    > <span data-ttu-id="d48ce-118">若要設定 listener 屬性的值，請使用與屬性 (property) 同名的屬性 (attribute)，而名稱中的所有字母都是小寫。</span><span class="sxs-lookup"><span data-stu-id="d48ce-118">To set the value of a listener property, use an attribute that has the same name as the property, with all letters in the name lowercase.</span></span> <span data-ttu-id="d48ce-119">例如，`location` 和 `customlocation` 屬性會設定 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> 和 <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> 屬性的值。</span><span class="sxs-lookup"><span data-stu-id="d48ce-119">For example, the `location` and `customlocation` attributes set the values of the <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.Location%2A> and <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener.CustomLocation%2A> properties.</span></span>

### <a name="to-write-event-information-to-the-file-log"></a><span data-ttu-id="d48ce-120">將事件資訊寫入檔案記錄檔</span><span class="sxs-lookup"><span data-stu-id="d48ce-120">To write event information to the file log</span></span>

<span data-ttu-id="d48ce-121">使用 `My.Application.Log.WriteEntry` 或 `My.Application.Log.WriteException` 方法，將資訊寫入檔案記錄檔。</span><span class="sxs-lookup"><span data-stu-id="d48ce-121">Use the `My.Application.Log.WriteEntry` or `My.Application.Log.WriteException` method to write information to the file log.</span></span> <span data-ttu-id="d48ce-122">如需詳細資訊，請參閱[如何：寫入記錄訊息](how-to-write-log-messages.md)和[如何：記錄例外狀況](how-to-log-exceptions.md)。</span><span class="sxs-lookup"><span data-stu-id="d48ce-122">For more information, see [How to: Write Log Messages](how-to-write-log-messages.md) and [How to: Log Exceptions](how-to-log-exceptions.md).</span></span>

<span data-ttu-id="d48ce-123">設定組件的檔案記錄檔接聽程式之後，接聽程式會接收 `My.Application.Log` 從該組件寫入的所有訊息。</span><span class="sxs-lookup"><span data-stu-id="d48ce-123">After you configure the file log listener for an assembly, it receives all messages that `My.Application.Log` writes from that assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="d48ce-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d48ce-124">See also</span></span>

- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteEntry%2A>
- <xref:Microsoft.VisualBasic.Logging.Log.WriteException%2A>
- [<span data-ttu-id="d48ce-125">使用應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="d48ce-125">Working with Application Logs</span></span>](working-with-application-logs.md)
- [<span data-ttu-id="d48ce-126">作法：記錄例外狀況</span><span class="sxs-lookup"><span data-stu-id="d48ce-126">How to: Log Exceptions</span></span>](how-to-log-exceptions.md)
