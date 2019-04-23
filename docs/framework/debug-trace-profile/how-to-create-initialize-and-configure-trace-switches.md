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
ms.openlocfilehash: 87170035df47e7605d25531df4b0759bf121ad80
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59325705"
---
# <a name="how-to-create-initialize-and-configure-trace-switches"></a>HOW TO：建立、初始化和設定追蹤參數
追蹤參數可讓您啟用、停用和篩選追蹤輸出。  
  
<a name="create"></a>   
## <a name="creating-and-initializing-a-trace-switch"></a>建立和初始化追蹤參數  
 為了使用追蹤參數，您必須先建立追蹤參數，並將其置於程式碼中。 您可從兩種預先定義的類別來建立參數物件：<xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> 類別和 <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> 類別。 如果您只在意是否要顯示追蹤訊息，則可使用 <xref:System.Diagnostics.BooleanSwitch>；如果您想要區別追蹤層級，請使用 <xref:System.Diagnostics.TraceSwitch>。 如果您使用 <xref:System.Diagnostics.TraceSwitch>，則可定義您自己的偵錯訊息，並將其與不同的追蹤層級關聯。 您可使用這兩種類型的參數搭配追蹤或偵錯。 根據預設，<xref:System.Diagnostics.BooleanSwitch> 為停用狀態，而 <xref:System.Diagnostics.TraceSwitch> 會設定為層級 <xref:System.Diagnostics.TraceLevel.Off?displayProperty=nameWithType>。 您可以建立追蹤參數，並置於程式碼中任何可能需要使用的部分。  
  
 雖然您可在程式碼中設定追蹤層級和其他組態選項，但是建議您使用組態檔來管理參數的狀態。 這是因為在組態系統中管理參數的組態讓您擁有更多的彈性，也就是說，您可開啟或關閉各種參數和變更層級，而不需要重新編譯應用程式。  
  
#### <a name="to-create-and-initialize-a-trace-switch"></a>建立和初始化追蹤參數  
  
1. 將參數定義為 <xref:System.Diagnostics.BooleanSwitch?displayProperty=nameWithType> 類型或 <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType> 類型，並設定參數的名稱和描述。  
  
2. 設定追蹤參數。 如需詳細資訊，請參閱[設定追蹤參數](#configure)。  
  
     下列程式碼會建立兩個參數，每種類型各一個：  
  
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
## <a name="configuring-trace-switches"></a>設定追蹤參數  
 在散發應用程式之後，您仍然可透過設定應用程式中的追蹤參數，來啟用或停用追蹤輸出。 設定參數表示在初始化參數之後，從外部來源變更其值。 您可以使用組態檔，來變更參數物件的值。 您可以設定開啟或關閉追蹤參數，或設定其層級，並決定要一起傳送至接聽程式的訊息數量和類型。  
  
 參數是使用 .config 檔案來設定的。 若為 Web 應用程式，這會是與專案關聯的 Web.config 檔案。 在 Windows 應用程式中，這個檔案的名稱為 (應用程式名稱).exe.config。在部署的應用程式中，這個檔案必須與可執行檔位於相同的資料夾中。  
  
 當應用程式第一次執行建立參數執行個體的程式碼時，會檢查組態檔是否有具名參數的相關追蹤層級資訊。 追蹤系統只會檢查一次組態檔是否有任何特定參數，也就是在應用程式第一次建立參數時。  
  
 在部署的應用程式中，您可以在應用程式未執行時，透過重新設定參數物件來啟用追蹤程式碼。 這通常涉及開啟和關閉參數物件，或是變更追蹤層級，然後再重新啟動應用程式。  
  
 當您建立參數的執行個體時，也可以透過指定下列兩個引數來初始化執行個體：*displayName* 引數和 *description* 引數。 建構函式的 *displayName* 引數會設定 <xref:System.Diagnostics.Switch> 類別執行個體的 <xref:System.Diagnostics.Switch.DisplayName%2A?displayProperty=nameWithType> 屬性。 *displayName* 是用來在 .config 檔案中設定參數的名稱，而 *description* 引數則應傳回參數的簡短描述和其控制的訊息。  
  
 除了指定要設定的參數名稱之外，您也必須指定參數的值。 這個值是整數。 如果是 <xref:System.Diagnostics.BooleanSwitch>，0 值會對應至 **Off**，而任何非零值則對應至 **On**。 如果是 <xref:System.Diagnostics.TraceSwitch>，0、1、2、3 和 4 分別對應至 **Off**、**Error**、**Warning**、**Info** 和 **Verbose**。 大於 4 的任何數字都會視為 **Verbose**，而小於零的任何數字則會視為 **Off**。  
  
> [!NOTE]
>  在 .NET Framework 2.0 版中，您可以使用文字來指定參數的值。 例如，<xref:System.Diagnostics.BooleanSwitch> 的 `true`，或是代表列舉值的文字 (例如 <xref:System.Diagnostics.TraceSwitch> 的 `Error`)。 `<add name="myTraceSwitch" value="Error" />` 這一行相當於 `<add name="myTraceSwitch" value="1" />`。  
  
 為了讓終端使用者能夠設定應用程式的追蹤參數，您必須在應用程式中提供有關參數的詳細文件。 您應詳述參數類型及其控制項目，以及如何開啟和關閉參數。 您也應為使用者提供 .config 檔案，以在註解中提供適當的說明。  
  
#### <a name="to-configure-trace-switches"></a>設定追蹤參數  
  
1. 若要使用追蹤參數，您必須先加以建立，並放在您的程式碼中，方法如[建立和初始化追蹤參數](#create)一節中所述。  
  
2. 如果您的專案未包含組態檔 (app.config 或 Web.config)，請從 [專案] 功能表中選取 [新增項目]。  
  
    -   **Visual Basic:** 在 **加入新項目**對話方塊方塊中，選擇**應用程式組態檔**。  
  
         隨即會建立並開啟應用程式組態檔。 這是根項目為 `<configuration>.` 的 XML 文件。  
  
    -   **視覺化C#:** 在 **加入新項目**對話方塊方塊中，選擇**XML 檔案**。 將這個檔案命名為 **app.config**。在 XML 編輯器中，於 XML 宣告後加入下列 XML：  
  
        ```xml  
        <configuration>  
        </configuration>  
        ```  
  
         在編譯專案之後，app.config 檔案會複製到專案輸出資料夾，並重新命名為 *applicationname*.exe.config。  
  
3. 在 `<configuration>` 標記後及 `</configuration>` 標記前，新增適當的 XML 以設定參數。 下列範例使用 `DataMessageSwitch` 的 **DisplayName** 屬性來示範 **BooleanSwitch**，並使用 `TraceLevelSwitch` 的 **DisplayName** 屬性來示範 **TraceSwitch**。  
  
    ```xml  
    <system.diagnostics>  
       <switches>  
          <add name="DataMessagesSwitch" value="0" />  
          <add name="TraceLevelSwitch" value="0" />  
       </switches>  
    </system.diagnostics>  
    ```  
  
     在這個組態中，這兩個參數都是關閉狀態。  
  
4. 如果您需要開啟 **BooleanSwitch**，例如先前範例中顯示的 `DataMessagesSwitch`，請將 **Value** 變更為任何非 0 的整數。  
  
5. 如果您需要開啟 **TraceSwitch**，例如先前範例中顯示的 `TraceLevelSwitch`，請將 **Value** 變更為適當的層級設定 (1 至 4)。  
  
6. 將註解加入 .config 檔案，讓終端使用者清楚了解要變更哪個值以適當設定參數。  
  
     下列範例顯示最後程式碼 (包含註解) 可能的樣子：  
  
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
  
## <a name="see-also"></a>另請參閱

- [追蹤和檢測應用程式](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
- [如何：將追蹤陳述式新增至應用程式程式碼](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)
- [追蹤參數](../../../docs/framework/debug-trace-profile/trace-switches.md)
- [追蹤和偵錯設定結構描述](../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
