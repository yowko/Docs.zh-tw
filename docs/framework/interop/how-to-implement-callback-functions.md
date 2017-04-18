---
title: "如何：實作回呼函式 | Microsoft Docs"
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
  - "callback 函式, 實作"
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：實作回呼函式
下列程序及範例示範 Managed 應用程式 \(使用平台叫用\) 如何將每個視窗的控制碼值列印到本機電腦上。  具體而言，程序和範例會使用 **EnumWindows** 函式以逐步執行視窗的清單，及使用 Managed 回撥函式 \(具名回撥\) 以列印視窗控制代碼的值。  
  
### 若要實作回撥函式  
  
1.  進一步進行實作前，請先查看 **EnumWindows** 函式的簽章。  **EnumWindows** 具有下列簽章：  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     此函式需要進行回撥的一個線索在於 **lpEnumFunc** 引數。  **lp** \(長度指標\) 前置詞與 **Func** 後置字元的結合，出現在引數名稱中是相當普遍的，其會將指標帶到回撥函式。  如需 Win32 函式的相關文件，請參閱 Microsoft Platform SDK。  
  
2.  建立 Managed 回撥函式。  此範例會宣告稱為 `CallBack` 的委派類型，其採用兩個引數 \(**hwnd** 和 **lparam**\)。  第一個引數是視窗的控制代碼；第二個引數則由應用程式定義。  在此版本中，兩個引數都必須是整數。  
  
     回撥函式通常傳回非零值即表示成功，傳回零則表示失敗。  此範例將傳回的值明確地設為 **true** 以繼續列舉。  
  
3.  建立委派，並將以引數方式傳遞至 **EnumWindows** 函式。  平台叫用會自動將委派轉換成熟悉的回撥格式。  
  
4.  請確定記憶體回收行程不會在回撥函式完成其工作前，回收該委派。  當您將委派以參數 \(或結構中的欄位\) 方式傳遞時，其將在呼叫期間保持為未回收。  因此，在以下列舉範例中，回撥函式在呼叫傳回前即會完成該工作，且不需要 Managed 呼叫端進行額外的動作。  
  
     但是，如果呼叫傳回後仍然可以叫用回撥函式，則 Managed 呼叫端必須採取步驟，以確保在回撥函式結束前，委派仍保持未回收。  如需取得不要進行記憶體回收的詳細資訊，請參閱 [Interop 封送處理](../../../docs/framework/interop/interop-marshaling.md)與平台叫用。  
  
## 範例  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
  
Public Delegate Function CallBack( _  
hwnd As Integer, lParam As Integer) As Boolean  
  
Public Class EnumReportApp  
  
    Declare Function EnumWindows Lib "user32" ( _  
       x As CallBack, y As Integer) As Integer  
  
    Public Shared Sub Main()  
        EnumWindows(AddressOf EnumReportApp.Report, 0)  
    End Sub 'Main  
  
    Public Shared Function Report(hwnd As Integer, lParam As Integer) _  
    As Boolean  
        Console.Write("Window handle is ")  
        Console.WriteLine(hwnd)  
        Return True  
    End Function 'Report  
End Class 'EnumReportApp  
  
```  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public delegate bool CallBack(int hwnd, int lParam);  
  
public class EnumReportApp  
{  
    [DllImport("user32")]  
    public static extern int EnumWindows(CallBack x, int y);   
  
    public static void Main()   
    {  
        CallBack myCallBack = new CallBack(EnumReportApp.Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    public static bool Report(int hwnd, int lParam)  
    {   
        Console.Write("Window handle is ");  
        Console.WriteLine(hwnd);  
        return true;  
    }  
}  
  
```  
  
```cpp  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
// A delegate type.  
delegate bool CallBack(int hwnd, int lParam);  
  
// Managed type with the method to call.  
ref class EnumReport  
{  
// Report the window handle.  
public:  
    [DllImport("user32")]  
    static int EnumWindows(CallBack^ x, int y);  
  
    static void Main()  
    {  
        EnumReport^ er = gcnew EnumReport;  
        CallBack^ myCallBack = gcnew CallBack(&EnumReport::Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    static bool Report(int hwnd, int lParam)  
    {  
       Console::Write(L"Window handle is ");  
       Console::WriteLine(hwnd);  
       return true;  
    }  
};  
  
int main()  
{  
    EnumReport::Main();  
}  
```  
  
## 請參閱  
 [回呼函式](../../../docs/framework/interop/callback-functions.md)   
 [呼叫 DLL 函式](../../../docs/framework/interop/calling-a-dll-function.md)