---
title: 使用 Assert 方法
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- granting permissions, overriding security checks
- code access security, overriding security checks
- overriding security checks
- security [.NET Framework], overriding security checks
- security [.NET Framework], assertions
- asserted permissions
- Assert method
- caller security checks
- permissions [.NET Framework], overriding security checks
- permissions [.NET Framework], assertions
ms.assetid: 1e40f4d3-fb7d-4f19-b334-b6076d469ea9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ea8be23eb6fd2500e59527890b874b8f19ec06d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397867"
---
# <a name="using-the-assert-method"></a>使用 Assert 方法
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A> 是一種方法，可以在程式碼存取權限類別以及 <xref:System.Security.PermissionSet> 類別上呼叫。 您可以使用**Assert**啟用您的程式碼 （和下游的呼叫端） 來執行您的程式碼有權執行的動作，但其呼叫端可能沒有權限。 安全性判斷提示會變更執行階段在安全性檢查期間執行的一般程序。 當您判斷提示權限時，它會告訴安全性系統不要檢查已判斷提示權限的程式碼呼叫端。  
  
> [!CAUTION]
>  請小心使用判斷提示，因為它們可能會開啟安全性漏洞，破壞的執行階段強制執行安全性限制的機制。  
  
 判斷提示適用於程式庫呼叫 Unmanaged 程式碼，或呼叫需要與程式庫預期用途不明顯相關的權限時。 例如，所有受管理的程式碼呼叫 unmanaged 程式碼必須具備**SecurityPermission**與**UnmanagedCode**指定旗標。 非來自本機電腦的程式碼，例如從近端內部網路下載的程式碼，預設不會授與此權限。 因此，為了讓從近端內部網路下載的程式碼，能夠呼叫使用 Unmanaged 程式碼的程式庫，它必須具備由程式庫判斷提示的權限。 此外，某些程式庫可能會進行呼叫端看不到且需要特殊權限的呼叫。  
  
 您也可以在您的程式碼存取資源時完全向呼叫端隱藏的情況下使用判斷提示。 例如，假設您的程式庫從資料庫取得資訊，但在過程中也從電腦登錄中讀取資訊。 使用您的程式庫的開發人員不必存取您的來源，因為它們有無從得知其程式碼需要**RegistryPermission**才能使用您的程式碼。 在此情況下，如果您認為要求程式碼呼叫端必須擁有存取登錄的權限是不合理或不必要的，可以判斷提示讀取登錄的權限。 在此情況下，便適合程式庫判斷提示權限，而不該呼叫端**RegistryPermission**可以使用程式庫。  
  
 只有在已判斷提示的權限和下游呼叫端需要的權限屬於相同類型，且需要的權限是判斷提示權限的子集時，判斷提示才會影響堆疊查核行程。 例如，如果您判斷提示**FileIOPermission**讀取 C 磁碟機，而下游需要的所有檔案進行**FileIOPermission**讀取 C:\Temp 中的檔案，判斷提示可能會影響堆疊查核行程;不過，如果是需要**FileIOPermission**以寫入 C 磁碟機，判斷提示會有任何影響。  
  
 若要執行判斷提示，您的程式碼必須同時被授與您正在判斷提示的權限，和表示進行判斷提示之權限的 <xref:System.Security.Permissions.SecurityPermission>。 雖然您可以判斷提示您的程式碼尚未被授與的權限，但判斷提示會毫無意義，因為安全性檢查會在判斷提示可能導致它成功之前就先失敗。  
  
 下圖顯示當您使用時，會發生什麼事**Assert**。 假設以下有關組件 A、B、C、E 和 F，以及 P1 和 P1A 兩個權限的陳述成立：  
  
-   P1A 代表讀取 C 磁碟機上 .txt 檔案的權限。  
  
-   P1 代表讀取 C 磁碟機上所有檔案的權限。  
  
-   P1A 和 P1 都**FileIOPermission**類型，且 P1A 為 P1 的子集。  
  
-   組件 E 和 F 已被授與 P1A 權限。  
  
-   組件 C 已被授與 P1 權限。  
  
-   組件 A 和 B 未被授與 P1 或 P1A 權限。  
  
-   方法 A 包含在組件 A 中，方法 B 包含在組件 B 中，依此類推。  
  
 ![](../../../docs/framework/misc/media/assert.gif "判斷提示")  
使用判斷提示  
  
 這個案例中，方法 A 呼叫 B、 B 呼叫 C、 C 呼叫 E，與 E 呼叫 f 方法 C 判斷提示讀取 C 磁碟機 （權限 P1），檔案的權限讀取 C 磁碟機 （權限 P1A） 上的.txt 檔案的方法 E 要求權限。 在執行階段遇到 F 中的需求時，堆疊查核行程，檢查 F 所有呼叫端的權限執行開頭 E E 已授與 P1A 權限，因此堆疊查核行程繼續檢查的 C，發現 C 的判斷提示的位置的權限。 因為需要的權限 (P1A) 是判斷提示權限 (P1) 的子集，堆疊查核行程會停止，且安全性檢查會自動成功。 組件 A 和 B 未被授與權限 P1A 並不重要。 藉由判斷提示 P1，C 方法可確保其呼叫者可以存取 P1 保護的資源，即使呼叫端未獲得存取該資源的權限亦然。  
  
 如果您設計類別程式庫，而類別會存取受保護的資源，在大部分情況下，您應該提出安全性需求，要求類別的呼叫端具有適當的權限。 如果類別接著執行的操作您知道其呼叫端大多不會具有權限，以及如果您願意為讓這些呼叫端呼叫您的程式碼負責，您可以判斷提示權限藉由呼叫**Assert**表示作業的權限物件上方法的程式碼正在執行。 使用**Assert**以這種方式通常無法這樣可讓呼叫端呼叫您的程式碼。 因此，如果您判斷提示權限，便務必要先執行適當的安全性檢查，以防止您的元件遭到誤用。  
  
 例如，假設您受高度信任的程式庫類別具有刪除檔案的方法。 它會藉由呼叫 Unmanaged 的 Win32 函式來存取檔案。 呼叫端叫用您的程式碼**刪除**方法，並傳入要刪除的檔案名稱 C:\Test.txt。 內**刪除**方法，您的程式碼會建立<xref:System.Security.Permissions.FileIOPermission>物件，代表 C:\Test.txt 的寫入權限。 (必須要有寫入權限才能刪除檔案。)您的程式碼接著會叫用命令式安全性檢查藉由呼叫**FileIOPermission**物件的**需求**方法。 如果呼叫堆疊中的其中一個呼叫端沒有這個權限，就會擲回 <xref:System.Security.SecurityException>。 如果未擲回任何例外狀況，您便知道所有呼叫端都擁有存取 C:\Test.txt 的權限。 因為您相信大部分的呼叫端不會具有存取 unmanaged 程式碼的權限，您的程式碼接著會建立<xref:System.Security.Permissions.SecurityPermission>物件，代表呼叫 unmanaged 程式碼的權限，並呼叫物件的**Assert**方法。 最後，它會呼叫 Unmanaged 的 Win32 函式，刪除 C:\Text.txt，並將控制權傳回給呼叫端。  
  
> [!CAUTION]
>  您必須確定您的程式碼使用判斷提示時，不會是程式碼可以供其他程式碼用來存取由您正在判斷提示之權限所保護的資源的情況。 例如，在寫入至檔案，其名稱由呼叫端做為參數指定的程式碼，您不會判斷提示**FileIOPermission**以寫入檔案，因為您的程式碼遭到第三者的誤用。  
  
 當您使用命令式安全性語法時，呼叫**Assert**相同方法中的多個權限的方法會導致擲回安全性例外狀況。 相反地，您應該建立**PermissionSet**物件，請將它傳遞您想要叫用，然後再呼叫個別的權限**Assert**方法**PermissionSet**物件。 您可以呼叫**Assert**方法超過一次當您使用宣告式安全性語法。  
  
 下列範例示範宣告式語法，覆寫安全性檢查使用**Assert**方法。 請注意， **FileIOPermissionAttribute**語法採用兩個值：<xref:System.Security.Permissions.SecurityAction>列舉型別和位置的檔案或目錄是要授與權限。 呼叫**Assert**會造成需要存取`C:\Log.txt`成功，即使呼叫端不會檢查用於存取檔案的使用權限。  
  
```vb  
Option Explicit  
Option Strict  
  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
  
      End Sub  
  
     <FileIOPermission(SecurityAction.Assert, All := "C:\Log.txt")> Public Sub   
      MakeLog()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now) '  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      [FileIOPermission(SecurityAction.Assert, All = @"C:\Log.txt")]  
      public void MakeLog()  
      {     
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}   
```  
  
 下列程式碼片段顯示的命令式語法，覆寫安全性檢查使用**Assert**方法。 在此範例中，執行個體**FileIOPermission**宣告物件。 其建構函式會傳遞**FileIOPermissionAccess.AllAccess**以定義類型的存取權限允許，後面接著描述檔案的位置的字串。 一次**FileIOPermission**物件定義，您只需要呼叫其**Assert**方法覆寫安全性檢查。  
  
```vb  
Option Explicit  
Option Strict  
Imports System  
Imports System.IO  
Imports System.Security.Permissions  
Namespace LogUtil  
   Public Class Log  
      Public Sub New()  
      End Sub 'New  
  
      Public Sub MakeLog()  
         Dim FilePermission As New FileIOPermission(FileIOPermissionAccess.AllAccess, "C:\Log.txt")  
         FilePermission.Assert()  
         Dim TextStream As New StreamWriter("C:\Log.txt")  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now)  
         TextStream.Close()  
      End Sub  
   End Class  
End Namespace  
```  
  
```csharp  
namespace LogUtil  
{  
   using System;  
   using System.IO;  
   using System.Security.Permissions;  
  
   public class Log  
   {  
      public Log()  
      {      
      }     
      public void MakeLog()  
      {  
         FileIOPermission FilePermission = new FileIOPermission(FileIOPermissionAccess.AllAccess,@"C:\Log.txt");   
         FilePermission.Assert();  
         StreamWriter TextStream = new StreamWriter(@"C:\Log.txt");  
         TextStream.WriteLine("This  Log was created on {0}", DateTime.Now);  
         TextStream.Close();  
      }  
   }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Security.PermissionSet>  
 <xref:System.Security.Permissions.SecurityPermission>  
 <xref:System.Security.Permissions.FileIOPermission>  
 <xref:System.Security.Permissions.SecurityAction>  
 [屬性](../../../docs/standard/attributes/index.md)  
 [程式碼存取安全性](../../../docs/framework/misc/code-access-security.md)
