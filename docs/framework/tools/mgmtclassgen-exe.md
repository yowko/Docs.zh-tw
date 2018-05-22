---
title: Mgmtclassgen.exe (管理強類型類別產生器)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 282d6376b434121ed6d59297be2ce36ce361c589
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a>Mgmtclassgen.exe (管理強類型類別產生器)
[管理強類型類別產生器] 工具可快速地為指定的 Windows Management Instrumentation (WMI) 類別產生早期繫結 Managed 類別。 產生的類別會將為存取 WMI 類別之執行個體所撰寫的程式碼加以簡化。  
  
## <a name="syntax"></a>語法  
  
```  
mgmtclassgen   
WMIClass [options]   
```  
  
|引數|描述|  
|--------------|-----------------|  
|*WMIClass*|要產生早期繫結 Managed 類別的 Windows Management Instrumentation 類別。|  
  
|選項|描述|  
|------------|-----------------|  
|**/l**  *language*|指定要用來產生早期繫結 Managed 類別的語言。 您可以指定 **CS** (C#，預設)、**VB** (Visual Basic)、**MC** (C++) 或 **JS** (JScript) 作為語言引數。|  
|**/m**  <電腦>|指定要連接的電腦，其中內含 WMI 類別。 預設為本機電腦。|  
|**/n**  *path*|指定包含 WMI 類別之 WMI 命名空間的路徑。 如果沒有指定這個選項，則工具預設會產生 **Root\cimv2** 命名空間之 *WMIClass* 的程式碼。|  
|**/o**  <類別命名空間>|指定要產生 Managed 程式碼類別的 .NET 命名空間。 如果沒有指定這個選項，則工具會產生使用 WMI 命名空間和結構描述前置詞的命名空間。 結構描述前置詞是位在底線字元前之類別名稱的一部分。 例如，針對 **Root\cimv2** 命名空間中的 **Win32_OperatingSystem** 類別，工具會在 **ROOT.CIMV2.Win32** 中產生類別。|  
|**/p**  <檔案路徑>|指定用來儲存所產生之程式碼的檔案路徑。 如果沒有指定這個選項，工具會將檔案建立在目前的目錄下。 工具會使用 *WMIClass* 引數來為其產生類別的類別和檔案命名。 類別和檔案的名稱和 *WMIClass.* 的名稱一樣。 如果 *WMIClass* 內含一個底線字元，工具會使用底線字元之後的類別名稱部分。 例如，如果 *WMIClass* 名稱的格式為 **Win32_LogicalDisk**，則產生的類別和檔案將會命名為 "logicaldisk"。 如果檔案已存在，工具會覆寫現有的檔案。|  
|**/pw**  <密碼>|透過 **/m** 選項指定登入電腦時要使用的密碼。|  
|**/u**  <使用者名稱>|透過 **/m** 選項指定登入電腦時要使用的使用者名稱。|  
|**/?**|顯示工具的命令語法和選項。|  
  
## <a name="remarks"></a>備註  
 Mgmtclassgen.exe 會使用 <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType> 方法。 因此，您可以使用任何自訂程式碼提供者來產生 Managed 語言 (不是 C#、Visual Basic 和 JScript) 的程式碼。  
  
 請注意，產生的類別會繫結至為其所產生的結構描述。 當基礎結構描述改變時，若要反映結構描述的這些改變就必須重新產生類別。  
  
 下表顯示 WMI 通用訊息模型 (Common Information Model，CIM) 類型如何對應至所產生類別中的資料類型：  
  
|CIM 類型|所產生之類別中的資料類型|  
|--------------|--------------------------------------|  
|CIM_SINT8|**SByte**|  
|CIM_UINT8|**Byte**|  
|CIM_SINT16|**Int16**|  
|CIM_UINT16|**UInt16**|  
|CIM_SINT32|**Int32**|  
|SIM_UINT32|**UInt32**|  
|CIM_SINT64|**Int64**|  
|CIM_UINT64|**UInt64**|  
|CIM_REAL32|**Single**|  
|CIM_REAL64|**Double**|  
|CIM_BOOLEAN|**布林值**|  
|CIM_String|**String**|  
|CIM_DATETIME|**DateTime** 或 **TimeSpan**|  
|CIM_REFERENCE|**ManagementPath**|  
|CIM_CHAR16|**Char**|  
|CIM_OBJECT|**ManagementBaseObject**|  
|CIM_IUNKNOWN|**物件**|  
|CIM_ARRAY|上述物件的陣列|  
  
 請注意下列在產生 WMI 類別時的行為：  
  
-   標準公用屬性或方法有可能和現有屬性或方法的名稱相同。 當此情況發生時，工具會變更在所產生之類別中屬性或方法的名稱以避免命名衝突。  
  
-   所產生之類別中屬性或方法的名稱有可能是目標程式語言的關鍵字。 當此情況發生時，工具會變更在所產生之類別中屬性或方法的名稱以避免命名衝突。  
  
-   在 WMI 中，限定詞為修飾詞，其中包含說明類別、執行個體、屬性或方法的資訊。 WMI 使用如 **Read**、**Write** 和 **Key** 等標準限定詞以說明產生之類別中的屬性。 例如，以 **Read** 限定詞修飾的屬性只能以在所產生類別中的屬性 **get** 存取子來定義。 因為以 **Read** 限定詞標記的屬性是做唯讀之用，不會定義 **set** 存取子。  
  
-   數值屬性可使用 **Values** 和 **ValueMaps** 限定詞加以修飾，表示屬性只能設定為指定的允許值。 列舉是以這些 **Values** 和 **ValueMaps** 產生的，而屬性會對應到列舉。  
  
-   WMI 使用單一 (Singleton) 這個詞彙來說明只能有一個執行個體的類別。 因此，單一 (Singleton) 類別的預設建構函式會將類別初始化為類別的唯一執行個體。  
  
-   WMI 類別可以擁有物件的屬性。 當產生此類型之 WMI 類別的強類型類別時，應考慮產生此內嵌物件屬性類型的強類型類別。 這能讓您以強類型的方式存取內嵌物件。 請注意，產生的程式碼可能無法偵測內嵌物件的類型。 在這個情況下，會在產生的程式碼中建立註解以告知您這個問題。 接著，您可以將所產生程式碼的屬性類型修改為其他所產生類別的屬性類型。  
  
-   WMI 中，CIM_DATETIME 資料類型的資料值可表示特定的日期和時間，或表示時間間隔。 如果資料值代表日期和時間，所產生類別中的資料類型就會是 **DateTime**。 如果資料值代表時間間隔，則所產生類別中的資料類型就會是 **TimeSpan**。  
  
 您也可以使用 Visual Studio .NET 中的 Server Explorer Management Extension 來產生強類型類別。  
  
 如需 WMI 的詳細資訊，請參閱 Platform SDK 說明文件中的 **Windows Management Instrumentation** 主題。  
  
## <a name="examples"></a>範例  
 下列命令會在 **Root\cimv2** 命名空間中產生 **Win32_LogicalDisk** WMI 類別的 Managed 類別 (以 C# 程式碼撰寫)。 工具會將 Managed 類別寫入 c:\disk.cs 的原始程式檔，放在 **ROOT.CIMV2.Win32** 命名空間中。  
  
```  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 下列程式碼範例顯示如何以程式設計方式使用產生的類別。 首先，列舉類別的執行個體並印出路徑。 接下來，以 WMI 的執行個體建立要初始化所產生類別的執行個體。 `Process` 是為 **Win32_Process** 產生的類別，`LogicalDisk` 則是為 **Root\cimv2** 命名空間中 **Win32_LogicalDisk** 產生的類別。  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App     
   Public Shared Sub Main()        
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process     
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Management>  
 <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=nameWithType>  
 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType>  
 [工具](../../../docs/framework/tools/index.md)  
 [命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
