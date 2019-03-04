---
title: 建立自訂的記錄檔接聽程式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- custom log listeners
- My.Application.Log object, custom log listeners
ms.assetid: 0e019115-4b25-4820-afb1-af8c6e391698
ms.openlocfilehash: 6bd950b1648bdf0b0c4673f2a90d67086b338ecd
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974766"
---
# <a name="walkthrough-creating-custom-log-listeners-visual-basic"></a><span data-ttu-id="28a6e-102">逐步解說：建立自訂的記錄檔接聽程式 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="28a6e-102">Walkthrough: Creating Custom Log Listeners (Visual Basic)</span></span>
<span data-ttu-id="28a6e-103">本逐步解說示範如何建立自訂記錄檔接聽程式，並將它設定為接聽 `My.Application.Log` 物件的輸出。</span><span class="sxs-lookup"><span data-stu-id="28a6e-103">This walkthrough demonstrates how to create a custom log listener and configure it to listen to the output of the `My.Application.Log` object.</span></span>  
  
## <a name="getting-started"></a><span data-ttu-id="28a6e-104">快速入門</span><span class="sxs-lookup"><span data-stu-id="28a6e-104">Getting Started</span></span>  
 <span data-ttu-id="28a6e-105">記錄檔接聽程式必須繼承自 <xref:System.Diagnostics.TraceListener> 類別。</span><span class="sxs-lookup"><span data-stu-id="28a6e-105">Log listeners must inherit from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
#### <a name="to-create-the-listener"></a><span data-ttu-id="28a6e-106">若要建立接聽程式</span><span class="sxs-lookup"><span data-stu-id="28a6e-106">To create the listener</span></span>  
  
-   <span data-ttu-id="28a6e-107">在應用程式中，建立一個繼承自 <xref:System.Diagnostics.TraceListener>，且命名為 `SimpleListener` 的類別。</span><span class="sxs-lookup"><span data-stu-id="28a6e-107">In your application, create a class named `SimpleListener` that inherits from <xref:System.Diagnostics.TraceListener>.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#16)]  
  
     <span data-ttu-id="28a6e-108">基底類別所需的 <xref:System.Diagnostics.TraceListener.Write%2A> 和 <xref:System.Diagnostics.TraceListener.WriteLine%2A> 方法會呼叫 `MsgBox` 來顯示其輸入。</span><span class="sxs-lookup"><span data-stu-id="28a6e-108">The <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods, required by the base class, call `MsgBox` to display their input.</span></span>  
  
     <span data-ttu-id="28a6e-109"><xref:System.Security.Permissions.HostProtectionAttribute> 屬性會套用至 <xref:System.Diagnostics.TraceListener.Write%2A> 和 <xref:System.Diagnostics.TraceListener.WriteLine%2A> 方法，使其屬性符合基底類別方法。</span><span class="sxs-lookup"><span data-stu-id="28a6e-109">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is applied to the <xref:System.Diagnostics.TraceListener.Write%2A> and <xref:System.Diagnostics.TraceListener.WriteLine%2A> methods so that their attributes match the base class methods.</span></span> <span data-ttu-id="28a6e-110"><xref:System.Security.Permissions.HostProtectionAttribute> 屬性可讓執行程式碼的主機決定讓程式碼公開主機保護同步處理。</span><span class="sxs-lookup"><span data-stu-id="28a6e-110">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute allows the host that runs the code to determine that the code exposes host-protection synchronization.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="28a6e-111"><xref:System.Security.Permissions.HostProtectionAttribute> 屬性只適用於裝載通用語言執行平台以及實作主機保護的 Unmanaged 應用程式，例如 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="28a6e-111">The <xref:System.Security.Permissions.HostProtectionAttribute> attribute is effective only on unmanaged applications that host the common language runtime and that implement host protection, such as SQL Server.</span></span>  
  
 <span data-ttu-id="28a6e-112">為了確保 `My.Application.Log` 使用記錄檔接聽程式，您應該建立強式名稱的組件以包含記錄檔接聽程式。</span><span class="sxs-lookup"><span data-stu-id="28a6e-112">To ensure that `My.Application.Log` uses your log listener, you should strongly name the assembly that contains your log listener.</span></span>  
  
 <span data-ttu-id="28a6e-113">下一個程序提供一些簡單的步驟，以建立強式名稱的記錄檔接聽程式組件。</span><span class="sxs-lookup"><span data-stu-id="28a6e-113">The next procedure provides some simple steps for creating a strongly named log-listener assembly.</span></span> <span data-ttu-id="28a6e-114">如需詳細資訊，請參閱[建立和使用強式名稱的組件](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md)。</span><span class="sxs-lookup"><span data-stu-id="28a6e-114">For more information, see [Creating and Using Strong-Named Assemblies](../../../../framework/app-domains/create-and-use-strong-named-assemblies.md).</span></span>  
  
#### <a name="to-strongly-name-the-log-listener-assembly"></a><span data-ttu-id="28a6e-115">若要建立強式名稱的記錄檔接聽程式組件</span><span class="sxs-lookup"><span data-stu-id="28a6e-115">To strongly name the log-listener assembly</span></span>  
  
1.  <span data-ttu-id="28a6e-116">在 **方案總管**中選取專案。</span><span class="sxs-lookup"><span data-stu-id="28a6e-116">Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="28a6e-117">在 [ **專案** ] 功能表上，選擇 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="28a6e-117">On the **Project** menu, choose **Properties**.</span></span>   
  
2.  <span data-ttu-id="28a6e-118">按一下 [簽署]索引標籤。</span><span class="sxs-lookup"><span data-stu-id="28a6e-118">Click the **Signing** tab.</span></span>  
  
3.  <span data-ttu-id="28a6e-119">選取 [簽署組件]方塊。</span><span class="sxs-lookup"><span data-stu-id="28a6e-119">Select the **Sign the assembly** box.</span></span>  
  
4.  <span data-ttu-id="28a6e-120">在 [選擇強式名稱金鑰檔]下拉式清單中，選取 [\<新增…>]。</span><span class="sxs-lookup"><span data-stu-id="28a6e-120">Select **\<New>** from the **Choose a strong name key file** drop-down list.</span></span>  
  
     <span data-ttu-id="28a6e-121">隨即開啟 [建立強式名稱金鑰]對話方塊。</span><span class="sxs-lookup"><span data-stu-id="28a6e-121">The **Create Strong Name Key** dialog box opens.</span></span>  
  
5.  <span data-ttu-id="28a6e-122">在 [金鑰檔案名稱]方塊中，提供金鑰檔名稱。</span><span class="sxs-lookup"><span data-stu-id="28a6e-122">Provide a name for the key file in the **Key file name** box.</span></span>  
  
6.  <span data-ttu-id="28a6e-123">將密碼輸入 [輸入密碼] 和 [確認密碼] 方塊。</span><span class="sxs-lookup"><span data-stu-id="28a6e-123">Enter a password in the **Enter password** and **Confirm password** boxes.</span></span>  
  
7.  <span data-ttu-id="28a6e-124">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="28a6e-124">Click **OK**.</span></span>  
  
8.  <span data-ttu-id="28a6e-125">重建應用程式。</span><span class="sxs-lookup"><span data-stu-id="28a6e-125">Rebuild the application.</span></span>  
  
## <a name="adding-the-listener"></a><span data-ttu-id="28a6e-126">新增接聽程式</span><span class="sxs-lookup"><span data-stu-id="28a6e-126">Adding the Listener</span></span>  
 <span data-ttu-id="28a6e-127">現在，組件已具有強式名稱，您必須決定接聽程式的強式名稱，以讓 `My.Application.Log` 使用您的記錄檔接聽程式。</span><span class="sxs-lookup"><span data-stu-id="28a6e-127">Now that the assembly has a strong name, you need to determine the strong name of the listener so that `My.Application.Log` uses your log listener.</span></span>  
  
 <span data-ttu-id="28a6e-128">具備強式名稱的類型格式如下：</span><span class="sxs-lookup"><span data-stu-id="28a6e-128">The format of a strongly named type is as follows.</span></span>  
  
 <span data-ttu-id="28a6e-129">\<類型名稱>, \<組件名稱>, \<版本號碼>, \<文化特性>, \<強式名稱></span><span class="sxs-lookup"><span data-stu-id="28a6e-129">\<type name>, \<assembly name>, \<version number>, \<culture>, \<strong name></span></span>  
  
#### <a name="to-determine-the-strong-name-of-the-listener"></a><span data-ttu-id="28a6e-130">若要決定接聽程式的強式名稱</span><span class="sxs-lookup"><span data-stu-id="28a6e-130">To determine the strong name of the listener</span></span>  
  
-   <span data-ttu-id="28a6e-131">下列程式碼示範如何決定以強式名稱命名 `SimpleListener` 的類型名稱。</span><span class="sxs-lookup"><span data-stu-id="28a6e-131">The following code shows how to determine the strongly named type name for `SimpleListener`.</span></span>  
  
     [!code-vb[VbVbalrMyApplicationLog#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyApplicationLog/VB/Form1.vb#17)]  
  
     <span data-ttu-id="28a6e-132">強式名稱的類型取決於您的專案而定。</span><span class="sxs-lookup"><span data-stu-id="28a6e-132">The strong name of the type depends on your project.</span></span>  
  
 <span data-ttu-id="28a6e-133">使用強式名稱時，您可以將接聽程式新增至 `My.Application.Log` 記錄檔接聽程式集合。</span><span class="sxs-lookup"><span data-stu-id="28a6e-133">With the strong name, you can add the listener to the `My.Application.Log` log-listener collection.</span></span>  
  
#### <a name="to-add-the-listener-to-myapplicationlog"></a><span data-ttu-id="28a6e-134">若要將接聽程式新增至 My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="28a6e-134">To add the listener to My.Application.Log</span></span>  
  
1.  <span data-ttu-id="28a6e-135">在方案總管中，以滑鼠右鍵按一下 app.config，並選擇 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="28a6e-135">Right-click on app.config in the **Solution Explorer** and choose **Open**.</span></span>  
  
     <span data-ttu-id="28a6e-136">-或-</span><span class="sxs-lookup"><span data-stu-id="28a6e-136">-or-</span></span>  
  
     <span data-ttu-id="28a6e-137">如果已有 app.config 檔案︰</span><span class="sxs-lookup"><span data-stu-id="28a6e-137">If there is an app.config file:</span></span>  
  
    1.  <span data-ttu-id="28a6e-138">在 [ **專案** ] 功能表中，選擇 [ **加入新項目**]。</span><span class="sxs-lookup"><span data-stu-id="28a6e-138">On the **Project** menu, choose **Add New Item**.</span></span>  
  
    2.  <span data-ttu-id="28a6e-139">在 [加入新項目]  對話方塊中，選擇 [應用程式組態檔] 。</span><span class="sxs-lookup"><span data-stu-id="28a6e-139">From the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
    3.  <span data-ttu-id="28a6e-140">按一下 [加入] 。</span><span class="sxs-lookup"><span data-stu-id="28a6e-140">Click **Add**.</span></span>  
  
2.  <span data-ttu-id="28a6e-141">在 `<listeners>` 區段下，具有 `<source>` 屬性 "DefaultSource" 的 `name` 區段中找出 `<sources>` 區段。</span><span class="sxs-lookup"><span data-stu-id="28a6e-141">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="28a6e-142">`<sources>` 區段位於最上層 `<system.diagnostics>` 區段中的 `<configuration>` 區段內。</span><span class="sxs-lookup"><span data-stu-id="28a6e-142">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
3.  <span data-ttu-id="28a6e-143">將此項目新增至 `<listeners>` 區段：</span><span class="sxs-lookup"><span data-stu-id="28a6e-143">Add this element to the `<listeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" />  
    ```  
  
4.  <span data-ttu-id="28a6e-144">找出位於最上層 `<sharedListeners>` 區段中 `<system.diagnostics>` 區段的 `<configuration>` 區段。</span><span class="sxs-lookup"><span data-stu-id="28a6e-144">Locate the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="28a6e-145">將此項目加入至該 `<sharedListeners>` 區段︰</span><span class="sxs-lookup"><span data-stu-id="28a6e-145">Add this element to that `<sharedListeners>` section:</span></span>  
  
    ```xml  
    <add name="SimpleLog" type="SimpleLogStrongName" />  
    ```  
  
     <span data-ttu-id="28a6e-146">將 `SimpleLogStrongName` 的值變更為接聽程式的強式名稱。</span><span class="sxs-lookup"><span data-stu-id="28a6e-146">Change the value of `SimpleLogStrongName` to be the strong name of the listener.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28a6e-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28a6e-147">See also</span></span>
- <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>
- [<span data-ttu-id="28a6e-148">使用應用程式記錄檔</span><span class="sxs-lookup"><span data-stu-id="28a6e-148">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)
- [<span data-ttu-id="28a6e-149">如何：記錄例外狀況</span><span class="sxs-lookup"><span data-stu-id="28a6e-149">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)
- [<span data-ttu-id="28a6e-150">如何：寫入記錄檔訊息</span><span class="sxs-lookup"><span data-stu-id="28a6e-150">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)
- [<span data-ttu-id="28a6e-151">逐步解說：變更 My.Application.Log 寫入資訊的位置</span><span class="sxs-lookup"><span data-stu-id="28a6e-151">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)
