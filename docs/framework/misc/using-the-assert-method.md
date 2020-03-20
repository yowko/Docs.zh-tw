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
ms.openlocfilehash: 92e49af78d42f360d5798a72d4e7b981295947e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181097"
---
# <a name="using-the-assert-method"></a>使用 Assert 方法
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A> 是一種方法，可以在程式碼存取權限類別以及 <xref:System.Security.PermissionSet> 類別上呼叫。 可以使用**Assert**使代碼（和下游調用方）執行代碼有權執行的操作，但其調用方可能無權執行操作。 安全性判斷提示會變更執行階段在安全性檢查期間執行的一般程序。 當您判斷提示權限時，它會告訴安全性系統不要檢查已判斷提示權限的程式碼呼叫端。  
  
> [!CAUTION]
> 請小心使用判斷提示，因為它們可能會開啟安全性漏洞，破壞的執行階段強制執行安全性限制的機制。  
  
 判斷提示適用於程式庫呼叫 Unmanaged 程式碼，或呼叫需要與程式庫預期用途不明顯相關的權限時。 例如，調用非託管代碼的所有託管代碼都必須具有指定**非託管代碼**標誌**的安全許可權**。 非來自本機電腦的程式碼，例如從近端內部網路下載的程式碼，預設不會授與此權限。 因此，為了讓從近端內部網路下載的程式碼，能夠呼叫使用 Unmanaged 程式碼的程式庫，它必須具備由程式庫判斷提示的權限。 此外，某些程式庫可能會進行呼叫端看不到且需要特殊權限的呼叫。  
  
 您也可以在您的程式碼存取資源時完全向呼叫端隱藏的情況下使用判斷提示。 例如，假設您的程式庫從資料庫取得資訊，但在過程中也從電腦登錄中讀取資訊。 由於使用庫的開發人員無法訪問您的原始程式碼，因此他們無法知道他們的代碼需要**註冊表許可權**才能使用您的代碼。 在此情況下，如果您認為要求程式碼呼叫端必須擁有存取登錄的權限是不合理或不必要的，可以判斷提示讀取登錄的權限。 在此情況下，庫應斷言許可權，以便沒有**註冊表許可權**的調用方可以使用該庫。  
  
 只有在已判斷提示的權限和下游呼叫端需要的權限屬於相同類型，且需要的權限是判斷提示權限的子集時，判斷提示才會影響堆疊查核行程。 例如，如果斷言**FileIO 許可**讀取 C 磁碟機上的所有檔，並且對**FileIO 許可**讀取 C：_Temp 中的檔提出了下游要求，則斷言可能會影響堆疊遍歷;如果斷言允許檔在 C 上讀取檔，則斷言可能會影響堆疊遍歷。但是，如果要求**FileIO 許可**寫入 C 磁碟機，則斷言將不起作用。  
  
 若要執行判斷提示，您的程式碼必須同時被授與您正在判斷提示的權限，和表示進行判斷提示之權限的 <xref:System.Security.Permissions.SecurityPermission>。 雖然您可以判斷提示您的程式碼尚未被授與的權限，但判斷提示會毫無意義，因為安全性檢查會在判斷提示可能導致它成功之前就先失敗。  
  
 下圖顯示了使用**斷言**時發生的情況。 假設以下有關組件 A、B、C、E 和 F，以及 P1 和 P1A 兩個權限的陳述成立：  
  
- P1A 代表讀取 C 磁碟機上 .txt 檔案的權限。  
  
- P1 代表讀取 C 磁碟機上所有檔案的權限。  
  
- P1A 和 P1 都是**FileIO 許可權**類型，P1A 是 P1 的子集。  
  
- 組件 E 和 F 已被授與 P1A 權限。  
  
- 組件 C 已被授與 P1 權限。  
  
- 組件 A 和 B 未被授與 P1 或 P1A 權限。  
  
- 方法 A 包含在組件 A 中，方法 B 包含在組件 B 中，依此類推。  
  
 ![顯示 Assert 方法程式集的圖。](./media/using-the-assert-method/assert-method-assemblies.gif)
  
 在這種情況下，方法 A 調用 B、B 調用 C、C 調用 E 和 E 調用 F. 方法 C 主張讀取 C 磁碟機上的檔的許可權（許可權 P1），方法 E 請求讀取 C 磁碟機上的 .txt 檔的許可權（許可權 P1A）。 在運行時遇到 F 中的需求時，將執行堆疊遍歷以檢查 F 的所有調用方的許可權，從 E. E 開始已被授予 P1A 許可權，因此堆疊遍歷將繼續檢查 C 的許可權，其中發現 C 的斷言。 因為需要的權限 (P1A) 是判斷提示權限 (P1) 的子集，堆疊查核行程會停止，且安全性檢查會自動成功。 組件 A 和 B 未被授與權限 P1A 並不重要。 藉由判斷提示 P1，C 方法可確保其呼叫者可以存取 P1 保護的資源，即使呼叫端未獲得存取該資源的權限亦然。  
  
 如果您設計類別程式庫，而類別會存取受保護的資源，在大部分情況下，您應該提出安全性需求，要求類別的呼叫端具有適當的權限。 如果類隨後執行一個操作，您知道其大多數調用方將沒有許可權，並且如果您願意承擔讓這些調用方調用代碼的責任，則可以通過在表示代碼執行的操作的權限物件上調用**Assert**方法來斷言許可權。 以這種方式使用**Assert**可以讓通常無法這樣做的調用方調用您的代碼。 因此，如果您判斷提示權限，便務必要先執行適當的安全性檢查，以防止您的元件遭到誤用。  
  
 例如，假設您受高度信任的程式庫類別具有刪除檔案的方法。 它會藉由呼叫 Unmanaged 的 Win32 函式來存取檔案。 調用方調用代碼的**Delete**方法，傳入要刪除的檔的名稱 C：_Test.txt。 在**Delete**方法中，代碼將<xref:System.Security.Permissions.FileIOPermission>創建一個表示對 C：_Test.txt 的寫入存取權限的物件。 （刪除檔需要寫入存取權限。然後，代碼通過調用**FileIO許可**物件的**Demand**方法調用必要安全性檢查。 如果呼叫堆疊中的其中一個呼叫端沒有這個權限，就會擲回 <xref:System.Security.SecurityException>。 如果未擲回任何例外狀況，您便知道所有呼叫端都擁有存取 C:\Test.txt 的權限。 由於您認為大多數調用方將無權訪問非託管代碼，因此代碼隨後創建一個<xref:System.Security.Permissions.SecurityPermission>物件，表示調用非託管代碼並調用物件的**Assert**方法的許可權。 最後，它會呼叫 Unmanaged 的 Win32 函式，刪除 C:\Text.txt，並將控制權傳回給呼叫端。  
  
> [!CAUTION]
> 您必須確定您的程式碼使用判斷提示時，不會是程式碼可以供其他程式碼用來存取由您正在判斷提示之權限所保護的資源的情況。 例如，在寫入其名稱由調用方指定為參數的檔的代碼中，不會斷言**FileIO 許可**以寫入檔，因為代碼可能會被協力廠商誤用。  
  
 使用命令性安全語法時，在同一方法中的多個許可權上調用**Assert**方法會導致引發安全異常。 相反，您應該創建一個**許可權集**物件，傳遞要調用的單個許可權，然後在**許可權集**物件上調用**Assert**方法。 使用聲明性安全語法時，可以多次調用**Assert**方法。  
  
 下面的示例顯示了使用**Assert**方法重寫安全檢查的聲明性語法。 請注意 **，FileIOEe屬性**語法採用兩個<xref:System.Security.Permissions.SecurityAction>值：枚舉和要授予許可權的檔或目錄的位置。 對**Assert**的調用會導致訪問`C:\Log.txt`成功，即使未檢查調用方訪問檔的許可權。  
  
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
  
 以下代碼片段顯示了使用**Assert**方法重寫安全檢查的必用語法。 在此示例中，聲明**FileIO許可**物件的實例。 其建構函式傳遞**FileIOAccess.AllAccess**來定義允許的訪問類型，然後是描述檔位置的字串。 定義**FileIO許可**物件後，只需調用其**Assert**方法來覆蓋安全檢查。  
  
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

- <xref:System.Security.PermissionSet>
- <xref:System.Security.Permissions.SecurityPermission>
- <xref:System.Security.Permissions.FileIOPermission>
- <xref:System.Security.Permissions.SecurityAction>
- [屬性](../../standard/attributes/index.md)
- [代碼訪問安全性](code-access-security.md)
