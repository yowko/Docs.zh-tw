---
title: "How to: Compile Conditionally with Trace and Debug | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "trace compiler options"
  - "trace statements"
  - "compiling source code, trace statements"
  - "tracing [.NET Framework], enabling or disabling"
  - "tracing [.NET Framework], compiling conditionally"
  - "TRACE directive"
  - "conditional compilation, tracing code"
ms.assetid: 56d051c3-012c-42c1-9a58-7270edc624aa
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Compile Conditionally with Trace and Debug
當您於開發期間偵錯應用程式時，追蹤及偵錯輸出都會移至 Visual Studio 中的 \[輸出\] 視窗。  然而，若要在已部署的應用程式中包含追蹤功能，您必須在啟用 **TRACE** 編譯器指示詞的情況下來編譯已經過檢測的應用程式。  這可將追蹤程式碼編譯成應用程式的發行版本。  如果您沒有啟用 **TRACE** 指示詞，則在編譯期間會忽略所有的追蹤程式碼，並且不會在您將部署的可執行程式碼中包含追蹤程式碼。  
  
 追蹤和偵錯方法均具有相關聯的Conditional 屬性。  例如，如果追蹤的 Conditional 屬性為 **true**，則會在組件 \(已編譯的 .exe 檔案或 .dll\) 中包含所有的追蹤陳述式，如果 **Trace** 條件屬性為 **false**，則不會包含追蹤陳述式。  
  
 您可以為組件開啟 **Trace** 或 **Debug** Conditional 屬性，或兩者都開啟或都關閉。  因此，組建可分為四種類型：**Debug**、**Trace**、兩者都開啟或兩者都關閉。  部分產品部署的發行組建可能不含兩者；大部分的偵錯組建則包含兩者。  
  
 您可用數種方式來指定應用程式的編譯器設定：  
  
-   屬性頁  
  
-   命令列  
  
-   **\#CONST** \(若為 Visual Basic\) 和 **\#define** \(若為 C\#\)  
  
### 從屬性頁對話方塊變更編譯設定  
  
1.  在 \[方案總管\] 中的專案節點上按一下滑鼠右鍵。  
  
2.  從捷徑功能表選擇 \[屬性\]。  
  
    -   在 Visual Basic 中，按一下屬性頁左窗格內的 \[編譯\] 索引標籤，然後按一下 \[進階編譯選項\] 按鈕，即可顯示 \[進階編譯器設定\] 對話方塊。  請選取您想要啟用之編譯器設定的核取方塊。  清除您想要停用之設定值的核取方塊。  
  
    -   在 C\# 中，按一下屬性頁左窗格內的 \[建置\] 索引標籤，然後選取您想要啟用之編譯器設定的核取方塊。  清除您想要停用之設定值的核取方塊。  
  
### 使用命令列來編譯已經過檢測的程式碼  
  
1.  在命令列上設定條件式編譯器參數。  編譯器會在可執行檔中包含追蹤或偵錯程式碼。  
  
     例如，在命令列上輸入下列編譯器指令會在已編譯可執行檔中包含追蹤程式碼：  
  
     若為 Visual Basic：**vbc \/r:System.dll \/d:TRACE\=TRUE \/d:DEBUG\=FALSE MyApplication.vb**  
  
     若為 C\#：**csc \/r:System.dll \/d:TRACE \/d:DEBUG\=FALSE MyApplication.cs**  
  
    > [!TIP]
    >  若要編譯一個以上的應用程式檔案，請在檔案名稱之間保留一個空格，例如，**MyApplication1.vb MyApplication2.vb MyApplication3.vb** 或 **MyApplication1.cs MyApplication2.cs MyApplication3.cs**。  
  
     上述範例中使用的條件式編譯指示詞的意義如下：  
  
    |指示詞|意義|  
    |---------|--------|  
    |`vbc`|Visual Basic 編譯器|  
    |`csc`|C\# 編譯器|  
    |`/r:`|參考外部組件 \(EXE 或 DLL\)|  
    |`/d:`|定義條件式編譯的符號|  
  
    > [!NOTE]
    >  您必須使用大寫字母來拼寫 TRACE 或 DEBUG。  如需條件式編譯命令的詳細資訊，請在命令提示字元中輸入 `vbc /?` \(若為 Visual Basic\) 或 `csc /?` \(若為 C\#\)。  如需詳細資訊，請參閱[從命令列建置](../Topic/How%20to:%20Set%20Environment%20Variables%20for%20the%20Visual%20Studio%20Command%20Line.md) \(C\#\) 或[叫用命令列編譯器](../Topic/How%20to:%20Invoke%20the%20Command-Line%20Compiler%20\(Visual%20Basic\).md) \(Visual Basic\)。  
  
### 使用 \#CONST 或 \#define 來執行條件式編譯  
  
1.  請在原始程式碼檔案上方輸入適用於您的程式語言之陳述式。  
  
    |語言|陳述式|結果|  
    |--------|---------|--------|  
    |**Visual Basic**|**\#CONST TRACE \= true**|啟用追蹤|  
    ||**\#CONST TRACE \= false**|停用追蹤|  
    ||**\#CONST DEBUG \= true**|啟用偵錯|  
    ||**\#CONST DEBUG \= false**|停用偵錯|  
    |**C\#**|**\#define TRACE**|啟用追蹤|  
    ||**\#undef TRACE**|停用追蹤|  
    ||**\#define DEBUG**|啟用偵錯|  
    ||**\#undef DEBUG**|停用偵錯|  
  
### 若要停用追蹤或偵錯  
  
1.  請刪除原始程式碼中的編譯器指示詞。  
  
     \-或\-  
  
2.  將編譯器指示詞標為註解。  
  
    > [!NOTE]
    >  當您準備編譯時，您可從 \[建置\] 功能表選取 \[建置\]，或使用命令列方法 \(但不輸入 **d:**\) 來定義條件式編譯的符號。  
  
## 請參閱  
 [Tracing and Instrumenting Applications](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)   
 [How to: Create, Initialize and Configure Trace Switches](../../../docs/framework/debug-trace-profile/how-to-create-initialize-and-configure-trace-switches.md)   
 [Trace Switches](../../../docs/framework/debug-trace-profile/trace-switches.md)   
 [Trace Listeners](../../../docs/framework/debug-trace-profile/trace-listeners.md)   
 [How to: Add Trace Statements to Application Code](../../../docs/framework/debug-trace-profile/how-to-add-trace-statements-to-application-code.md)   
 [How to: Set Environment Variables for the Visual Studio Command Line](../Topic/How%20to:%20Set%20Environment%20Variables%20for%20the%20Visual%20Studio%20Command%20Line.md)   
 [How to: Invoke the Command\-Line Compiler](../Topic/How%20to:%20Invoke%20the%20Command-Line%20Compiler%20\(Visual%20Basic\).md)