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
ms.openlocfilehash: 5b5a13b362f565cfae9247908bcf3cf35c899ae4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910724"
---
# <a name="using-the-assert-method"></a>使用 Assert 方法
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
 <xref:System.Security.CodeAccessPermission.Assert%2A> 是一種方法，可以在程式碼存取權限類別以及 <xref:System.Security.PermissionSet> 類別上呼叫。 您可以使用**Assert**讓程式碼 (和下游呼叫端) 執行您的程式碼有權執行的動作, 但其呼叫端可能沒有許可權。 安全性判斷提示會變更執行階段在安全性檢查期間執行的一般程序。 當您判斷提示權限時，它會告訴安全性系統不要檢查已判斷提示權限的程式碼呼叫端。  
  
> [!CAUTION]
>  請小心使用判斷提示，因為它們可能會開啟安全性漏洞，破壞的執行階段強制執行安全性限制的機制。  
  
 判斷提示適用於程式庫呼叫 Unmanaged 程式碼，或呼叫需要與程式庫預期用途不明顯相關的權限時。 例如, 呼叫非受控碼的所有 managed 程式碼, 都必須具有指定的**UnmanagedCode**旗標的**SecurityPermission** 。 非來自本機電腦的程式碼，例如從近端內部網路下載的程式碼，預設不會授與此權限。 因此，為了讓從近端內部網路下載的程式碼，能夠呼叫使用 Unmanaged 程式碼的程式庫，它必須具備由程式庫判斷提示的權限。 此外，某些程式庫可能會進行呼叫端看不到且需要特殊權限的呼叫。  
  
 您也可以在您的程式碼存取資源時完全向呼叫端隱藏的情況下使用判斷提示。 例如，假設您的程式庫從資料庫取得資訊，但在過程中也從電腦登錄中讀取資訊。 因為使用您的程式庫的開發人員無法存取您的來源, 所以他們無法知道他們的程式碼需要**RegistryPermission**才能使用您的程式碼。 在此情況下，如果您認為要求程式碼呼叫端必須擁有存取登錄的權限是不合理或不必要的，可以判斷提示讀取登錄的權限。 在此情況下, 程式庫適用于判斷提示許可權, 讓沒有**RegistryPermission**的呼叫端可以使用程式庫。  
  
 只有在已判斷提示的權限和下游呼叫端需要的權限屬於相同類型，且需要的權限是判斷提示權限的子集時，判斷提示才會影響堆疊查核行程。 例如, 如果您判斷提示**FileIOPermission**以讀取 C 磁片磁碟機上的所有檔案, 並對**FileIOPermission**進行下游需求來讀取 C:\Temp 中的檔案, 則判斷提示可能會影響堆疊的進度。不過, 如果需要**FileIOPermission**寫入 C 磁片磁碟機, 則判斷提示不會有任何作用。  
  
 若要執行判斷提示，您的程式碼必須同時被授與您正在判斷提示的權限，和表示進行判斷提示之權限的 <xref:System.Security.Permissions.SecurityPermission>。 雖然您可以判斷提示您的程式碼尚未被授與的權限，但判斷提示會毫無意義，因為安全性檢查會在判斷提示可能導致它成功之前就先失敗。  
  
 下圖顯示當您使用**Assert**時, 會發生什麼事。 假設以下有關組件 A、B、C、E 和 F，以及 P1 和 P1A 兩個權限的陳述成立：  
  
- P1A 代表讀取 C 磁碟機上 .txt 檔案的權限。  
  
- P1 代表讀取 C 磁碟機上所有檔案的權限。  
  
- P1A 和 P1 兩者都是**FileIOPermission**類型, 而 P1A 則是 P1 的子集。  
  
- 組件 E 和 F 已被授與 P1A 權限。  
  
- 組件 C 已被授與 P1 權限。  
  
- 組件 A 和 B 未被授與 P1 或 P1A 權限。  
  
- 方法 A 包含在組件 A 中，方法 B 包含在組件 B 中，依此類推。  
  
 ![顯示 Assert 方法元件的圖表。](./media/using-the-assert-method/assert-method-assemblies.gif)    
  
 在此案例中, 方法 A 會呼叫 B, B 呼叫 C, C 呼叫 E, 而 E 呼叫 F。方法 C 會在 c 磁片磁碟機上讀取檔案的許可權 (許可權 P1), 而方法 E 會要求許可權以讀取 C 磁片磁碟機上的 .txt 檔案 (許可權 P1A)。 在執行時間遇到 F 中的需求時, 會執行堆疊逐步解說, 以檢查 F 的所有呼叫端的許可權, 從 E. E 開始已被授與 P1A 許可權, 因此堆疊逐步解說會繼續檢查 C 的許可權, 其中會探索 C 的判斷提示。 因為需要的權限 (P1A) 是判斷提示權限 (P1) 的子集，堆疊查核行程會停止，且安全性檢查會自動成功。 組件 A 和 B 未被授與權限 P1A 並不重要。 藉由判斷提示 P1，C 方法可確保其呼叫者可以存取 P1 保護的資源，即使呼叫端未獲得存取該資源的權限亦然。  
  
 如果您設計類別程式庫，而類別會存取受保護的資源，在大部分情況下，您應該提出安全性需求，要求類別的呼叫端具有適當的權限。 如果類別接著執行您知道大部分呼叫端都沒有許可權的作業, 而且您願意負責讓這些呼叫端呼叫您的程式碼, 您可以在上呼叫**assert**方法, 以判斷提示許可權。代表程式碼正在執行之作業的權限物件。 以這種方式使用**Assert** , 可讓通常無法執行此動作的呼叫端呼叫您的程式碼。 因此，如果您判斷提示權限，便務必要先執行適當的安全性檢查，以防止您的元件遭到誤用。  
  
 例如，假設您受高度信任的程式庫類別具有刪除檔案的方法。 它會藉由呼叫 Unmanaged 的 Win32 函式來存取檔案。 呼叫者叫用您程式碼的**Delete**方法, 並傳入要刪除之檔案的名稱, 對 c:\test.txt 在**Delete**方法中, 您的程式碼<xref:System.Security.Permissions.FileIOPermission>會建立代表對 c:\test.txt 寫入存取權的物件。 (必須要有寫入權限才能刪除檔案。)您的程式碼接著會藉由呼叫**FileIOPermission**物件的**Demand**方法, 叫用命令式安全性檢查。 如果呼叫堆疊中的其中一個呼叫端沒有這個權限，就會擲回 <xref:System.Security.SecurityException>。 如果未擲回任何例外狀況，您便知道所有呼叫端都擁有存取 C:\Test.txt 的權限。 因為您相信大部分的呼叫端都沒有存取非受控碼的許可權, 您的<xref:System.Security.Permissions.SecurityPermission>程式碼接著會建立物件, 代表呼叫非受控碼的許可權, 並呼叫物件的**Assert**方法。 最後，它會呼叫 Unmanaged 的 Win32 函式，刪除 C:\Text.txt，並將控制權傳回給呼叫端。  
  
> [!CAUTION]
>  您必須確定您的程式碼使用判斷提示時，不會是程式碼可以供其他程式碼用來存取由您正在判斷提示之權限所保護的資源的情況。 例如, 在寫入檔案的程式碼中, 呼叫者將其名稱指定為參數時, 您不會判斷提示**FileIOPermission**寫入檔案, 因為您的程式碼會開放給協力廠商誤用。  
  
 當您使用命令式安全性語法時, 針對相同方法中的多個許可權呼叫**Assert**方法, 會導致擲回安全性例外狀況。 相反地, 您應該建立**PermissionSet**物件, 將您要叫用的個別許可權傳遞給它, 然後在**PermissionSet**物件上呼叫**Assert**方法。 當您使用宣告式安全性語法時, 可以多次呼叫**Assert**方法。  
  
 下列範例顯示使用**Assert**方法覆寫安全性檢查的宣告式語法。 請注意, **system.security.permissions.fileiopermissionattribute.pathdiscovery**語法接受兩個值: <xref:System.Security.Permissions.SecurityAction>列舉, 以及要授與許可權之檔案或目錄的位置。 即使未檢查呼叫端是否有存取檔案`C:\Log.txt`的許可權, 對 Assert 的呼叫也會導致存取的要求成功。  
  
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
  
 下列程式碼片段顯示使用**Assert**方法覆寫安全性檢查的命令式語法。 在此範例中, 會宣告**FileIOPermission**物件的實例。 其會傳遞**FileIOPermissionAccess. AllAccess**來定義允許的存取類型, 後面接著描述檔案位置的字串。 定義**FileIOPermission**物件之後, 您只需要呼叫其**Assert**方法來覆寫安全性檢查。  
  
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
- [程式碼存取安全性](../../../docs/framework/misc/code-access-security.md)
