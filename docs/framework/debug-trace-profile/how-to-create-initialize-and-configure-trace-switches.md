---
title: HOW TO：建立、初始化和設定追蹤參數
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- trace switches, configuring
- tracing [.NET Framework], trace switches
- switches, trace
- tracing [.NET Framework], enabling or disabling
- Web.config configuration file, trace switches
ms.assetid: 5a0e41bf-f99c-4692-8799-f89617f5bcf9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d7b8551c8b82ca880d989a1b58411f9555a9feb4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079132"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a><span data-ttu-id="50e6f-102">HOW TO：建立、初始化和設定追蹤參數</span><span class="sxs-lookup"><span data-stu-id="50e6f-102">How to: Create, Initialize and Configure Trace Switches</span></span>
<span data-ttu-id="50e6f-103">追蹤參數可讓您啟用、停用和篩選追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="50e6f-103">Trace switches enable you to enable, disable, and filter tracing output.</span></span>  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a><span data-ttu-id="50e6f-104">建立和初始化追蹤參數</span><span class="sxs-lookup"><span data-stu-id="50e6f-104">Creating and initializing a trace switch</span></span>  
 <span data-ttu-id="50e6f-105">為了使用追蹤參數，您必須先建立追蹤參數，並將其置於程式碼中。</span><span class="sxs-lookup"><span data-stu-id="50e6f-105">In order to use trace switches, you must first create them and place them in your code.</span></span> <span data-ttu-id="50e6f-106">您可從兩種預先定義的類別來建立參數物件：<xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> 類別和 <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> 類別。</span><span class="sxs-lookup"><span data-stu-id="50e6f-106">There are two predefined classes from which you can create switch objects: the <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> class and the <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="50e6f-107">如果您只在意是否要顯示追蹤訊息，則可使用 <xref:System.Diagnostics.BooleanSwitch>；如果您想要區別追蹤層級，請使用 <xref:System.Diagnostics.TraceSwitch>。</span><span class="sxs-lookup"><span data-stu-id="50e6f-107">You would use <xref:System.Diagnostics.BooleanSwitch> if you care only about whether or not a tracing message appears; you would use <xref:System.Diagnostics.TraceSwitch> if you want to discriminate between levels of tracing.</span></span> <span data-ttu-id="50e6f-108">如果您使用 <xref:System.Diagnostics.TraceSwitch>，則可定義您自己的偵錯訊息，並將其與不同的追蹤層級關聯。</span><span class="sxs-lookup"><span data-stu-id="50e6f-108">If you use a <xref:System.Diagnostics.TraceSwitch>, you can define your own debugging messages and associate them with different trace levels.</span></span> <span data-ttu-id="50e6f-109">您可使用這兩種類型的參數搭配追蹤或偵錯。</span><span class="sxs-lookup"><span data-stu-id="50e6f-109">You can use both types of switches with either tracing or debugging.</span></span> <span data-ttu-id="50e6f-110">根據預設，<xref:System.Diagnostics.BooleanSwitch> 為停用狀態，而 <xref:System.Diagnostics.TraceSwitch> 會設定為層級 <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="50e6f-110">By default, a <xref:System.Diagnostics.BooleanSwitch> is disabled and a <xref:System.Diagnostics.TraceSwitch> is set to level <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="50e6f-111">您可以建立追蹤參數，並置於程式碼中任何可能需要使用的部分。</span><span class="sxs-lookup"><span data-stu-id="50e6f-111">Trace switches can be created and placed in any part of your code that might use them.</span></span>  
  
 <span data-ttu-id="50e6f-112">雖然您可在程式碼中設定追蹤層級和其他組態選項，但是建議您使用組態檔來管理參數的狀態。</span><span class="sxs-lookup"><span data-stu-id="50e6f-112">Although you can set trace levels and other configuration options in code, we recommend that you use the configuration file to manage the state of your switches.</span></span> <span data-ttu-id="50e6f-113">這是因為在組態系統中管理參數的組態讓您擁有更多的彈性，也就是說，您可開啟或關閉各種參數和變更層級，而不需要重新編譯應用程式。</span><span class="sxs-lookup"><span data-stu-id="50e6f-113">This is because managing the configuration of your switches in the configuration system gives you greater flexibility — you can turn on and off various switches and change levels without recompiling your application.</span></span>  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a><span data-ttu-id="50e6f-114">建立和初始化追蹤參數</span><span class="sxs-lookup"><span data-stu-id="50e6f-114">To create and initialize a trace switch</span></span>  
  
1.  <span data-ttu-id="50e6f-115">將參數定義為 <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> 類型或 <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> 類型，並設定參數的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="50e6f-115">Define a switch as either type <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> or type <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> and set the name and description of the switch.</span></span>  
  
2.  <span data-ttu-id="50e6f-116">設定追蹤參數。</span><span class="sxs-lookup"><span data-stu-id="50e6f-116">Configure your trace switch.</span></span> <span data-ttu-id="50e6f-117">如需詳細資訊，請參閱[設定追蹤參數](#configure)。</span><span class="sxs-lookup"><span data-stu-id="50e6f-117">For more information, see [Configuring trace switches](#configure).</span></span>  
  
     <span data-ttu-id="50e6f-118">下列程式碼會建立兩個參數，每種類型各一個：</span><span class="sxs-lookup"><span data-stu-id="50e6f-118">The following code creates two switches, one of each type:</span></span>  
  
    ```vb  
    Dim dataSwitch As New BooleanSwitch("Data", "DataAccess module")  
    Dim generalSwitch As New TraceSwitch("General", "Entire application")  
    ```  
  
    ```csharp  
    System.Diagnostics.BooleanSwitch dataSwitch =   
       new System.Diagnostics.BooleanSwitch("Data", "DataAccess module");  
    System.Diagnostics.TraceSwitch generalSwitch =   
       new System.Diagnostics.TraceSwitch("General",   
       "Entire application");  
    ```  
  
<a name="configure"></a>   
## <a name="configuring-trace-switches"></a><span data-ttu-id="50e6f-119">設定追蹤參數</span><span class="sxs-lookup"><span data-stu-id="50e6f-119">Configuring trace switches</span></span>  
 <span data-ttu-id="50e6f-120">在散發應用程式之後，您仍然可透過設定應用程式中的追蹤參數，來啟用或停用追蹤輸出。</span><span class="sxs-lookup"><span data-stu-id="50e6f-120">After your application has been distributed, you can still enable or disable trace output by configuring the trace switches in your application.</span></span> <span data-ttu-id="50e6f-121">設定參數表示在初始化參數之後，從外部來源變更其值。</span><span class="sxs-lookup"><span data-stu-id="50e6f-121">Configuring a switch means changing its value from an external source after it has been initialized.</span></span> <span data-ttu-id="50e6f-122">您可以使用組態檔，來變更參數物件的值。</span><span class="sxs-lookup"><span data-stu-id="50e6f-122">You can change the values of the switch objects using the configuration file.</span></span> <span data-ttu-id="50e6f-123">您可以設定開啟或關閉追蹤參數，或設定其層級，並決定要一起傳送至接聽程式的訊息數量和類型。</span><span class="sxs-lookup"><span data-stu-id="50e6f-123">You configure a trace switch to turn it on and off, or to set its level, determining the amount and type of messages it passes along to listeners.</span></span>  
  
 <span data-ttu-id="50e6f-124">參數是使用 .config 檔案來設定的。</span><span class="sxs-lookup"><span data-stu-id="50e6f-124">Your switches are configured using the .config file.</span></span> <span data-ttu-id="50e6f-125">若為 Web 應用程式，這會是與專案關聯的 Web.config 檔案。</span><span class="sxs-lookup"><span data-stu-id="50e6f-125">For a Web application, this is the Web.config file associated with the project.</span></span> <span data-ttu-id="50e6f-126">在 Windows 應用程式中，這個檔案的名稱為 (應用程式名稱).exe.config。在部署的應用程式中，這個檔案必須與可執行檔位於相同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="50e6f-126">In a Windows application, this file is named (application name).exe.config. In a deployed application, this file must reside in the same folder as the executable.</span></span>  
  
 <span data-ttu-id="50e6f-127">當應用程式第一次執行建立參數執行個體的程式碼時，會檢查組態檔是否有具名參數的相關追蹤層級資訊。</span><span class="sxs-lookup"><span data-stu-id="50e6f-127">When your application executes the code that creates an instance of a switch for the first time, it checks the configuration file for trace-level information about the named switch.</span></span> <span data-ttu-id="50e6f-128">追蹤系統只會檢查一次組態檔是否有任何特定參數，也就是在應用程式第一次建立參數時。</span><span class="sxs-lookup"><span data-stu-id="50e6f-128">The tracing system examines the configuration file only once for any particular switch — the first time your application creates the switch.</span></span>  
  
 <span data-ttu-id="50e6f-129">在部署的應用程式中，您可以在應用程式未執行時，透過重新設定參數物件來啟用追蹤程式碼。</span><span class="sxs-lookup"><span data-stu-id="50e6f-129">In a deployed application, you enable trace code by reconfiguring switch objects when your application is not running.</span></span> <span data-ttu-id="50e6f-130">這通常涉及開啟和關閉參數物件，或是變更追蹤層級，然後再重新啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="50e6f-130">Typically this involves turning the switch objects on and off or by changing the tracing levels, and then restarting your application.</span></span>  
  
 <span data-ttu-id="50e6f-131">當您建立參數的執行個體時，也可以透過指定下列兩個引數來初始化執行個體：*displayName* 引數和 *description* 引數。</span><span class="sxs-lookup"><span data-stu-id="50e6f-131">When you create an instance of a switch, you also initialize it by specifying two arguments: a *displayName* argument and a *description* argument.</span></span> <span data-ttu-id="50e6f-132">建構函式的 *displayName* 引數會設定 <xref:System.Diagnostics.Switch> 類別執行個體的 <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> 屬性。</span><span class="sxs-lookup"><span data-stu-id="50e6f-132">The *displayName* argument of the constructor sets the <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> property of the <xref:System.Diagnostics.Switch> class instance.</span></span> <span data-ttu-id="50e6f-133">*displayName* 是用來在 .config 檔案中設定參數的名稱，而 *description* 引數則應傳回參數的簡短描述和其控制的訊息。</span><span class="sxs-lookup"><span data-stu-id="50e6f-133">The *displayName* is the name that is used to configure the switch in the .config file, and the *description* argument should return a brief description of the switch and what messages it controls.</span></span>  
  
 <span data-ttu-id="50e6f-134">除了指定要設定的參數名稱之外，您也必須指定參數的值。</span><span class="sxs-lookup"><span data-stu-id="50e6f-134">In addition to specifying the name of a switch to configure, you must also specify a value for the switch.</span></span> <span data-ttu-id="50e6f-135">這個值是整數。</span><span class="sxs-lookup"><span data-stu-id="50e6f-135">This value is an Integer.</span></span> <span data-ttu-id="50e6f-136">如果是 <xref:System.Diagnostics.BooleanSwitch>，0 值會對應至 **Off**，而任何非零值則對應至 **On**。</span><span class="sxs-lookup"><span data-stu-id="50e6f-136">For <xref:System.Diagnostics.BooleanSwitch>, a value of 0 corresponds to **Off**, and any nonzero value corresponds to **On**.</span></span> <span data-ttu-id="50e6f-137">如果是 <xref:System.Diagnostics.TraceSwitch>，0、1、2、3 和 4 分別對應至 **Off**、**Error**、**Warning**、**Info** 和 **Verbose**。</span><span class="sxs-lookup"><span data-stu-id="50e6f-137">For <xref:System.Diagnostics.TraceSwitch>, 0,1,2,3, and 4 correspond **Off**, **Error**, **Warning**, **Info**, and **Verbose**, respectively.</span></span> <span data-ttu-id="50e6f-138">大於 4 的任何數字都會視為 **Verbose**，而小於零的任何數字則會視為 **Off**。</span><span class="sxs-lookup"><span data-stu-id="50e6f-138">Any number greater than 4 is treated as **Verbose**, and any number less than zero is treated as **Off**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="50e6f-139">在 .NET Framework 2.0 版中，您可以使用文字來指定參數的值。</span><span class="sxs-lookup"><span data-stu-id="50e6f-139">In the .NET Framework version 2.0, you can use text to specify the value for a switch.</span></span> <span data-ttu-id="50e6f-140">例如，<xref:System.Diagnostics.BooleanSwitch> 的 `true`，或是代表列舉值的文字 (例如 <xref:System.Diagnostics.TraceSwitch> 的 `Error`)。</span><span class="sxs-lookup"><span data-stu-id="50e6f-140">For example, `true` for a <xref:System.Diagnostics.BooleanSwitch> or the text representing an enumeration value such as `Error` for a <xref:System.Diagnostics.TraceSwitch>.</span></span> <span data-ttu-id="50e6f-141">`<add name="myTraceSwitch" value="Error" />` 這一行相當於 `<add name="myTraceSwitch" value="1" />`。</span><span class="sxs-lookup"><span data-stu-id="50e6f-141">The line `<add name="myTraceSwitch" value="Error" />` is equivalent to `<add name="myTraceSwitch" value="1" />`.</span></span>  
  
 <span data-ttu-id="50e6f-142">為了讓終端使用者能夠設定應用程式的追蹤參數，您必須在應用程式中提供有關參數的詳細文件。</span><span class="sxs-lookup"><span data-stu-id="50e6f-142">In order for end users to be able to configure an application's trace switches, you must provide detailed documentation on the switches in your application.</span></span> <span data-ttu-id="50e6f-143">您應詳述參數類型及其控制項目，以及如何開啟和關閉參數。</span><span class="sxs-lookup"><span data-stu-id="50e6f-143">You should detail which switches control what and how to turn them on and off.</span></span> <span data-ttu-id="50e6f-144">您也應為使用者提供 .config 檔案，以在註解中提供適當的說明。</span><span class="sxs-lookup"><span data-stu-id="50e6f-144">You should also provide your end user with a .config file that has appropriate Help in the comments.</span></span>  
  
#### <a name="to-configure-trace-switches"></a><span data-ttu-id="50e6f-145">設定追蹤參數</span><span class="sxs-lookup"><span data-stu-id="50e6f-145">To configure trace switches</span></span>  
  
1.  <span data-ttu-id="50e6f-146">若要使用追蹤參數，您必須先加以建立，並放在您的程式碼中，方法如[建立和初始化追蹤參數](#create)一節中所述。</span><span class="sxs-lookup"><span data-stu-id="50e6f-146">In order to use trace switches, you must first create them and place them in your code as described in the section [Creating and initializing a trace switch](#create).</span></span>  
  
2.  <span data-ttu-id="50e6f-147">如果您的專案未包含組態檔 (app.config 或 Web.config)，請從 [專案] 功能表中選取 [新增項目]。</span><span class="sxs-lookup"><span data-stu-id="50e6f-147">If your project does not contain a configuration file (app.config or Web.config), then from the **Project** menu, select **Add New Item**.</span></span>  
  
    -   <span data-ttu-id="50e6f-148">**Visual Basic:** 在 **加入新項目**對話方塊方塊中，選擇**應用程式組態檔**。</span><span class="sxs-lookup"><span data-stu-id="50e6f-148">**Visual Basic:** In the **Add New Item** dialog box, choose **Application Configuration File**.</span></span>  
  
         <span data-ttu-id="50e6f-149">隨即會建立並開啟應用程式組態檔。</span><span class="sxs-lookup"><span data-stu-id="50e6f-149">The application configuration file is created and opened.</span></span> <span data-ttu-id="50e6f-150">這是其根項目是 XML 文件</span><span class="sxs-lookup"><span data-stu-id="50e6f-150">This is an XML document whose root element is</span></span> `<configuration>.`  
  
    -   <span data-ttu-id="50e6f-151">**視覺化C#:** 在 **加入新項目**對話方塊方塊中，選擇**XML 檔案**。</span><span class="sxs-lookup"><span data-stu-id="50e6f-151">**Visual C#:** In the **Add New Item** dialog box, choose **XML File**.</span></span> <span data-ttu-id="50e6f-152">將這個檔案命名為 **app.config**。在 XML 編輯器中，於 XML 宣告後加入下列 XML：</span><span class="sxs-lookup"><span data-stu-id="50e6f-152">Name this file **app.config**. In the XML editor, after the XML declaration, add the following XML:</span></span>  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         <span data-ttu-id="50e6f-153">在編譯專案之後，app.config 檔案會複製到專案輸出資料夾，並重新命名為 *applicationname*.exe.config。</span><span class="sxs-lookup"><span data-stu-id="50e6f-153">When your project is compiled, the app.config file is copied to the project output folder and is renamed *applicationname*.exe.config.</span></span>  
  
3.  <span data-ttu-id="50e6f-154">在 `<configuration>` 標記後及 `</configuration>` 標記前，新增適當的 XML 以設定參數。</span><span class="sxs-lookup"><span data-stu-id="50e6f-154">After the `<configuration>` tag but before the `</configuration>` tag, add the appropriate XML to configure your switches.</span></span> <span data-ttu-id="50e6f-155">下列範例使用 `DataMessageSwitch` 的 **DisplayName** 屬性來示範 **BooleanSwitch**，並使用 `TraceLevelSwitch` 的 **DisplayName** 屬性來示範 **TraceSwitch**。</span><span class="sxs-lookup"><span data-stu-id="50e6f-155">The following examples demonstrate a **BooleanSwitch** with a **DisplayName** property of `DataMessageSwitch` and a **TraceSwitch** with a **DisplayName** property of `TraceLevelSwitch`.</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     <span data-ttu-id="50e6f-156">在這個組態中，這兩個參數都是關閉狀態。</span><span class="sxs-lookup"><span data-stu-id="50e6f-156">In this configuration, both switches are off.</span></span>  
  
4.  <span data-ttu-id="50e6f-157">如果您需要開啟 **BooleanSwitch**，例如先前範例中顯示的 `DataMessagesSwitch`，請將 **Value** 變更為任何非 0 的整數。</span><span class="sxs-lookup"><span data-stu-id="50e6f-157">If you need to turn on a **BooleanSwitch**, such as `DataMessagesSwitch` shown in the previous example, change the **Value** to any integer other than 0.</span></span>  
  
5.  <span data-ttu-id="50e6f-158">如果您需要開啟 **TraceSwitch**，例如先前範例中顯示的 `TraceLevelSwitch`，請將 **Value** 變更為適當的層級設定 (1 至 4)。</span><span class="sxs-lookup"><span data-stu-id="50e6f-158">If you need to turn on a **TraceSwitch**, such as `TraceLevelSwitch` shown in the previous example, change the **Value** to the appropriate level setting (1 to 4).</span></span>  
  
6.  <span data-ttu-id="50e6f-159">將註解加入 .config 檔案，讓終端使用者清楚了解要變更哪個值以適當設定參數。</span><span class="sxs-lookup"><span data-stu-id="50e6f-159">Add comments to the .config file so the end user has a clear understanding of what values to change to configure the switches appropriately.</span></span>  
  
     <span data-ttu-id="50e6f-160">下列範例顯示最後程式碼 (包含註解) 可能的樣子：</span><span class="sxs-lookup"><span data-stu-id="50e6f-160">The following example shows how the final code, including comments, might look:</span></span>  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <!-- This switch controls data messages. In order to receive data   
             trace messages, change value="0" to value="1" -->  
          <add name="DataMessagesSwitch" value="0" />  
          <!-- This switch controls general messages. In order to   
             receive general trace messages change the value to the   
             appropriate level. "1" gives error messages, "2" gives errors   
             and warnings, "3" gives more detailed error information, and   
             "4" gives verbose trace information -->  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="50e6f-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50e6f-161">See also</span></span>

- [<span data-ttu-id="50e6f-162">追蹤和稽核應用程式</span><span class="sxs-lookup"><span data-stu-id="50e6f-162">Tracing and Instrumenting Applications</span></span>](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="50e6f-163">HOW TO：將追蹤陳述式新增至應用程式程式碼</span><span class="sxs-lookup"><span data-stu-id="50e6f-163">How to: Add Trace Statements to Application Code</span></span>](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [<span data-ttu-id="50e6f-164">追蹤參數</span><span class="sxs-lookup"><span data-stu-id="50e6f-164">Trace Switches</span></span>](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [<span data-ttu-id="50e6f-165">追蹤和偵錯設定結構描述</span><span class="sxs-lookup"><span data-stu-id="50e6f-165">Trace and Debug Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
