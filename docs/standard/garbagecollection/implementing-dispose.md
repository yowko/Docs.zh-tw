---
title: "實作 Dispose 方法"
description: "實作 Dispose 方法"
keywords: .NET, .NET Core
author: stevehoag
ms.author: shoag
manager: wpickett
ms.date: 08/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: eca6cdc3-6a14-4296-86fb-1eb2f21455b0
translationtype: Human Translation
ms.sourcegitcommit: b20713600d7c3ddc31be5885733a1e8910ede8c6
ms.openlocfilehash: fcb7944a7a9cce1cf23b42790133ee051c0e05f0

---

# <a name="implementing-a-dispose-method"></a>實作 Dispose 方法

您實作 [Dispose](xref:System.IDisposable.Dispose) 方法，以釋放您的應用程式所使用的 Unmanaged 資源。 .NET 記憶體回收行程不會配置或釋放 Unmanaged 記憶體。 

處置物件的模式稱為處置模式，會在物件的存留期上安排順序。 處置模式僅適用於存取 Unmanaged 資源的物件，例如檔案和管道控制碼、註冊控制代碼、等候控制代碼，或是 Unmanaged 記憶體區塊的指標。 這是因為記憶體回收行程在回收未使用的 Managed 物件方面相當有效率，但是它無法回收 Unmanaged 物件。

處置模式有兩種：

* 將類型使用的每一種 Unmanaged 資源包裝在安全控制代碼中 (也就是在衍生自 [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) 的類別中)。 在這種情況下，請實作 [IDisposable](xref:System.IDisposable) 介面和額外的 `Dispose(Boolean)` 方法。 這是建議的做法，這種做法不需要覆寫 [Object.Finalize](xref:System.Object.Finalize) 方法。 

> [!NOTE]
> [Microsoft.Win32.SafeHandles](xref:Microsoft.Win32.SafeHandles) 命名空間會提供一組衍生自 [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) 的類別，[使用安全控制代碼](#using-safe-handles)一節將列出這些類別。 如果您找不到適合釋放 Unmanaged 資源的類別，可以實作自有的 [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) 子類別。 
 
* 除了實作 [IDisposable](xref:System.IDisposable) 介面和額外的 `Dispose(Boolean`) 方法之外，還要覆寫 [Object.Finalize](xref:System.Object.Finalize) 方法。 您必須覆寫 [Finalize](xref:System.Object.Finalize)，才能確保類型消費者未呼叫您的 [IDisposable.Dispose](xref:System.IDisposable.Dispose) 實作時，Unmanaged 資源仍會獲得處置。 如果您採用前一項所討論的建議技術，[System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) 類別會自動為您完成這項作業。 

若要確保資源永遠都能適當清除，[Dispose](xref:System.IDisposable.Dispose) 方法應該能夠被呼叫多次而不會擲回例外狀況。 

提供的 [GC.KeepAlive](xref:System.GC.KeepAlive(System.Object)) 方法程式碼範例示範積極記憶體回收如何在被回收的物件仍在執行時，即讓完成項開始執行。 在冗長的 `Dispose` 方法結尾處呼叫 [KeepAlive](xref:System.GC.KeepAlive(System.Object)) 方法，這是個不錯的做法。

## <a name="dispose-and-disposeboolean"></a>Dispose() 和 Dispose(Boolean)

[IDisposable](xref:System.IDisposable) 介面要求實作單一無參數方法 [Dispose](xref:System.IDisposable.Dispose)。 不過，處置模式要求實作兩種 `Dispose` 方法： 

* 公用非虛擬 (在 Visual Basic 中為 `NonInheritable`) 的 [IDisposable.Dispose](xref:System.IDisposable.Dispose) 實作，而且沒有任何參數。

* 受保護的虛擬 (Visual Basic 中為 `Overridable`) `Dispose` 方法，其簽章為：

  ```cs
  protected virtual void Dispose(bool disposing)
  ```

  ```vb
  Protected Overridable Sub Dispose(disposing As Boolean)
  ```

### <a name="the-dispose-overload"></a>Dispose() 多載

由於這個公用、非虛擬 (在 Visual Basic 中為 `NonInheritable`)、無參數的 `Dispose` 方法是由類型消費者所呼叫，其用途是釋放 Unmanaged 資源並指出完成項 (如果有的話) 不需要執行。 因此，它擁有標準實作：

```cs
public void Dispose()
{
   // Dispose of unmanaged resources.
   Dispose(true);
   // Suppress finalization.
   GC.SuppressFinalize(this);
}
```

```vb
Public Sub Dispose() _
           Implements IDisposable.Dispose
   ' Dispose of unmanaged resources.
   Dispose(True)
   ' Suppress finalization.
   GC.SuppressFinalize(Me)
End Sub
```

`Dispose` 方法會執行所有物件清除，所以記憶體回收行程不需要再呼叫物件的 [Object.Finalize](xref:System.Object.Finalize) 覆寫。 因此，呼叫 [GC.SuppressFinalize](xref:System.GC.SuppressFinalize(System.Object)) 方法會防止記憶體回收行程執行完成項。 如果類型沒有完成項，則呼叫 [SuppressFinalize](xref:System.GC.SuppressFinalize(System.Object)) 沒有作用。 請注意，實際釋放 Unmanaged 資源的工作是由 `Dispose` 方法的第二個多載執行。

### <a name="the-disposeboolean-overload"></a>Dispose(Boolean) 多載

在第二個多載中，*disposing* 參數為 [Boolean](xref:System.Boolean)，它會指出方法呼叫是來自 [Dispose](xref:System.IDisposable.Dispose) 方法 (其值為 `true`) 或是來自完成項 (其值為 `false`)。 

方法的主體是由兩個程式碼區塊所構成： 

* 釋放 Unmanaged 資源的區塊。 不論 *disposing* 參數的值為何，這個區塊都會執行。 

* 釋放 Managed 資源的條件性區塊。 如果 *disposing* 的值為 `true`，這個區塊就會執行。 它所釋放的 Managed 資源可能包括： 

    **實作 IDisposable 的 Managed 物件**。 條件式區塊可以用來呼叫其 [Dispose](xref:System.IDisposable.Dispose) 實作。 如果您已使用安全控制代碼包裝 Unmanaged 資源，則應該在這裡呼叫 [SafeHandle.Dispose(Boolean](xref:System.Runtime.InteropServices.SafeHandle.Dispose(System.Boolean)) 實作。 

    **耗用大量記憶體或耗用少量資源的 Managed 物件。** 如果它們是之非由記憶體回收行程，在 `Dispose` 方法中明確釋放這些物件的速度，會比由記憶體回收行程以非決定性的方式回收來得快。 


如果方法呼叫來自完成項 (也就是如果 *disposing* 為 `false`)，則只會執行釋放 Unmanaged 資源的程式碼。 由於記憶體回收行程在最終處理期間終結 Managed 物件的順序並未定義，使用 `Dispose` 值呼叫此 `false` 多載可防止完成項嘗試釋放可能已經回收的 Managed 資源。 

## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>實作基底類別的處置模式

如果您實作基底類別的處置模式，則必須提供下列項目： 

> [!IMPORTANT]
> 您應該針對實作 [IDisposable](xref:System.IDisposable) 並且不是 `sealed` 的所有基底類別實作此模式。 
 
* 呼叫 [Dispose](xref:System.IDisposable.Dispose) 方法的 `Dispose(Boolean)` 實作。 

* 實際釋放資源的 `Dispose(Boolean)` 方法。 

* 衍生自包裝您的 Unmanaged 資源之 [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) 的類別 (建議使用)，或是 [Object.Finalize](xref:System.Object.Finalize) 方法的覆寫。 [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) 類別會提供完成項，讓您不必自行撰寫程式碼。 

以下一般模式將會實作使用安全控制代碼之基底類別的處置模式。 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.Runtime.InteropServices;

class BaseClass : IDisposable
{
   // Flag: Has Dispose already been called?
   bool disposed = false;
   // Instantiate a SafeHandle instance.
   SafeHandle handle = new SafeFileHandle(IntPtr.Zero, true);

   // Public implementation of Dispose pattern callable by consumers.
   public void Dispose()
   { 
      Dispose(true);
      GC.SuppressFinalize(this);           
   }

   // Protected implementation of Dispose pattern.
   protected virtual void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         handle.Dispose();
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //
      disposed = true;
   }
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.Runtime.InteropServices

Class BaseClass : Implements IDisposable
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False
   ' Instantiate a SafeHandle instance.
   Dim handle As SafeHandle = New SafeFileHandle(IntPtr.Zero, True)

   ' Public implementation of Dispose pattern callable by consumers.
   Public Sub Dispose() _
              Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)           
   End Sub

   ' Protected implementation of Dispose pattern.
   Protected Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         handle.Dispose()
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True
   End Sub
End Class
```

> [!NOTE] 
> 上一個範例使用 [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) 物件來說明模式；可改用任何衍生自 [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) 的物件。 請注意，該範例未正確地執行個體化其 [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) 物件。 
 
以下一般模式將會實作覆寫 [Object.Finalize](xref:System.Object.Finalize) 之基底類別的處置模式。 

```cs
using System;

class BaseClass : IDisposable
{
   // Flag: Has Dispose already been called?
   bool disposed = false;

   // Public implementation of Dispose pattern callable by consumers.
   public void Dispose()
   { 
      Dispose(true);
      GC.SuppressFinalize(this);           
   }

   // Protected implementation of Dispose pattern.
   protected virtual void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //
      disposed = true;
   }

   ~BaseClass()
   {
      Dispose(false);
   }
}
```

```vb
Class BaseClass : Implements IDisposable
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False

   ' Public implementation of Dispose pattern callable by consumers.
   Public Sub Dispose() _
              Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)           
   End Sub

   ' Protected implementation of Dispose pattern.
   Protected Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True
   End Sub

   Protected Overrides Sub Finalize()
      Dispose(False)      
   End Sub
End Class
```

> [!NOTE]
> 在 C# 中，您會透過定義 `destructor` 來覆寫 [Object.Finalize](xref:System.Object.Finalize)。 


## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>實作衍生類別的處置模式

從實作 [IDisposable](xref:System.IDisposable) 介面的類別衍生的類別不應該實作 [IDisposable](xref:System.IDisposable)，因為 [IDisposable.Dispose](xref:System.IDisposable.Dispose) 的基底類別實作會由其衍生類別繼承。 因此，若要實作衍生類別的處置模式，請改為提供下列項目： 

* 覆寫基底類別方法及實際釋放衍生類別之資源的 `protected Dispose(Boolean)` 方法。 這個方法也應該呼叫基底類別的 `Dispose(Boolean)` 方法，並且將 *disposing* 引數的 `true` 值傳遞給它。 

* 衍生自包裝您的 Unmanaged 資源之 [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) 的類別 (建議使用)，或是 [Object.Finalize](xref:System.Object.Finalize) 方法的覆寫。 [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) 類別會提供完成項，讓您不必自行撰寫程式碼。 如果您提供完成項，則它應該呼叫 `Dispose(Boolean)` 多載且 *disposing* 引數為 `false`。 

以下一般模式將會實作使用安全控制代碼之衍生類別的處置模式： 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.Runtime.InteropServices;

class DerivedClass : BaseClass
{
   // Flag: Has Dispose already been called?
   bool disposed = false;
   // Instantiate a SafeHandle instance.
   SafeHandle handle = new SafeFileHandle(IntPtr.Zero, true);

   // Protected implementation of Dispose pattern.
   protected override void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         handle.Dispose();
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //

      disposed = true;
      // Call base class implementation.
      base.Dispose(disposing);
   }
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.Runtime.InteropServices

Class DerivedClass : Inherits BaseClass 
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False
   ' Instantiate a SafeHandle instance.
   Dim handle As SafeHandle = New SafeFileHandle(IntPtr.Zero, True)

   ' Protected implementation of Dispose pattern.
   Protected Overrides Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         handle.Dispose()
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True

      ' Call base class implementation.
      MyBase.Dispose(disposing)
   End Sub
End Class
```

> [!NOTE] 
> 上一個範例使用 [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) 物件來說明模式；可改用任何衍生自 [SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) 的物件。 請注意，該範例未正確地執行個體化其 [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) 物件。 

以下一般模式將會實作覆寫 [Object.Finalize](xref:System.Object.Finalize) 之衍生類別的處置模式：

```cs
using System;

class DerivedClass : BaseClass
{
   // Flag: Has Dispose already been called?
   bool disposed = false;

   // Protected implementation of Dispose pattern.
   protected override void Dispose(bool disposing)
   {
      if (disposed)
         return; 

      if (disposing) {
         // Free any other managed objects here.
         //
      }

      // Free any unmanaged objects here.
      //
      disposed = true;

      // Call the base class implementation.
      base.Dispose(disposing);
   }

   ~DerivedClass()
   {
      Dispose(false);
   }
}
```

```vb
Class DerivedClass : Inherits BaseClass
   ' Flag: Has Dispose already been called?
   Dim disposed As Boolean = False

   ' Protected implementation of Dispose pattern.
   Protected Overrides Sub Dispose(disposing As Boolean)
      If disposed Then Return

      If disposing Then
         ' Free any other managed objects here.
         '
      End If

      ' Free any unmanaged objects here.
      '
      disposed = True

      ' Call the base class implementation.
      MyBase.Dispose(disposing)
   End Sub

   Protected Overrides Sub Finalize()
      Dispose(False)
   End Sub 
End Class
```

> [!NOTE]
> 在 C# 中，您會透過定義 `destructor` 來覆寫 [Object.Finalize](xref:System.Object.Finalize)。

## <a name="using-safe-handles"></a>使用安全控制代碼

撰寫物件完成項的程式碼是一項複雜的工作，若未正確撰寫，可能會造成問題。 因此，建議您建構 [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) 物件，而不要實作完成項。

衍生自 [System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle) 類別的類別會在不受干擾的情況下，藉由指派和釋放控制代碼的方式簡化物件存留期的問題。 這些類別包含重要的完成項，該完成項保證會在應用程式定義域卸載時執行。 [Microsoft.Win32.SafeHandles](xref:Microsoft.Win32.SafeHandles) 命名空間中的下列衍生類別會提供安全控制代碼： 

* [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle)、[SafeMemoryMappedFileHandle](xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle) 和 [SafePipeHandle](xref:Microsoft.Win32.SafeHandles.SafePipeHandle) 類別，適用於檔案、記憶體對應檔案和管道。 

* [SafeMemoryMappedViewHandle](xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle) 類別，適用於記憶體檢視。 

* [SafeNCryptKeyHandle](https://msdn.microsoft.com/en-us/library/microsoft.win32.safehandles.safencryptkeyhandle(v=vs.110).aspx)、[SafeNCryptProviderHandle](https://msdn.microsoft.com/en-us/library/microsoft.win32.safehandles.safencryptproviderhandle(v=vs.110).aspx) 和 [SafeNCryptSecretHandle](https://msdn.microsoft.com/en-us/library/microsoft.win32.safehandles.safencryptsecrethandle(v=vs.110).aspx) 類別，適用於加密建構。

* [SafeRegistryHandle](xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle) 類別，適用於登錄機碼。 

* [SafeWaitHandle](xref:Microsoft.Win32.SafeHandles.SafeWaitHandle) 類別，適用於等候控制代碼。 

## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>使用安全控制代碼實作基底類別的處置模式

下列範例將說明使用安全控制代碼封裝 Unmanaged 資源之基底類別 `DisposableStreamResource` 的處置模式。 它會定義 `DisposableResource` 類別，該類別使用 [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) 包裝代表開啟檔案的 [Stream](xref:System.IO.Stream) 物件。 `DisposableResource` 方法還包含單一屬性 `Size`，該屬性會傳回檔案資料流中的位元組總數。 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.IO;
using System.Runtime.InteropServices;

public class DisposableStreamResource : IDisposable
{
   // Define constants.
   protected const uint GENERIC_READ = 0x80000000;
   protected const uint FILE_SHARE_READ = 0x00000001;
   protected const uint OPEN_EXISTING = 3;
   protected const uint FILE_ATTRIBUTE_NORMAL = 0x80;
   protected IntPtr INVALID_HANDLE_VALUE = new IntPtr(-1);
   private const int INVALID_FILE_SIZE = unchecked((int) 0xFFFFFFFF);

   // Define Windows APIs.
   [DllImport("kernel32.dll", EntryPoint = "CreateFileW", CharSet = CharSet.Unicode)]
   protected static extern IntPtr CreateFile (
                                  string lpFileName, uint dwDesiredAccess, 
                                  uint dwShareMode, IntPtr lpSecurityAttributes, 
                                  uint dwCreationDisposition, uint dwFlagsAndAttributes, 
                                  IntPtr hTemplateFile);

   [DllImport("kernel32.dll")]
   private static extern int GetFileSize(SafeFileHandle hFile, out int lpFileSizeHigh);

   // Define locals.
   private bool disposed = false;
   private SafeFileHandle safeHandle; 
   private long bufferSize;
   private int upperWord;

   public DisposableStreamResource(string filename)
   {
      if (filename == null)
         throw new ArgumentNullException("The filename cannot be null.");
      else if (filename == "")
         throw new ArgumentException("The filename cannot be an empty string.");

      IntPtr handle = CreateFile(filename, GENERIC_READ, FILE_SHARE_READ,
                                 IntPtr.Zero, OPEN_EXISTING, FILE_ATTRIBUTE_NORMAL,
                                 IntPtr.Zero);
      if (handle != INVALID_HANDLE_VALUE)
         safeHandle = new SafeFileHandle(handle, true);
      else
         throw new FileNotFoundException(String.Format("Cannot open '{0}'", filename));

      // Get file size.
      bufferSize = GetFileSize(safeHandle, out upperWord); 
      if (bufferSize == INVALID_FILE_SIZE)
         bufferSize = -1;
      else if (upperWord > 0) 
         bufferSize = (((long)upperWord) << 32) + bufferSize;
   }

   public long Size 
   { get { return bufferSize; } }

   public void Dispose()
   {
      Dispose(true);
      GC.SuppressFinalize(this);
   }           

   protected virtual void Dispose(bool disposing)
   {
      if (disposed) return;

      // Dispose of managed resources here.
      if (disposing)
         safeHandle.Dispose();

      // Dispose of any unmanaged resources not wrapped in safe handles.

      disposed = true;
   }  
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.IO

Public Class DisposableStreamResource : Implements IDisposable
   ' Define constants.
   Protected Const GENERIC_READ As UInteger = &H80000000ui
   Protected Const FILE_SHARE_READ As UInteger = &H0000000i
   Protected Const OPEN_EXISTING As UInteger = 3
   Protected Const FILE_ATTRIBUTE_NORMAL As UInteger = &H80
   Protected INVALID_HANDLE_VALUE As New IntPtr(-1)
   Private Const INVALID_FILE_SIZE As Integer = &HFFFFFFFF

   ' Define Windows APIs.
   Protected Declare Function CreateFile Lib "kernel32" Alias "CreateFileA" (
                                         lpFileName As String, dwDesiredAccess As UInt32, 
                                         dwShareMode As UInt32, lpSecurityAttributes As IntPtr, 
                                         dwCreationDisposition As UInt32, dwFlagsAndAttributes As UInt32, 
                                         hTemplateFile As IntPtr) As IntPtr
   Private Declare Function GetFileSize Lib "kernel32" (hFile As SafeFileHandle, 
                                                        ByRef lpFileSizeHigh As Integer) As Integer

   ' Define locals.
   Private disposed As Boolean = False
   Private safeHandle As SafeFileHandle 
   Private bufferSize As Long 
   Private upperWord As Integer

   Public Sub New(filename As String)
      If filename Is Nothing Then
         Throw New ArgumentNullException("The filename cannot be null.")
      Else If filename = ""
         Throw New ArgumentException("The filename cannot be an empty string.")
      End If

      Dim handle As IntPtr = CreateFile(filename, GENERIC_READ, FILE_SHARE_READ,
                                        IntPtr.Zero, OPEN_EXISTING, FILE_ATTRIBUTE_NORMAL,
                                        IntPtr.Zero)
      If handle <> INVALID_HANDLE_VALUE Then
         safeHandle = New SafeFileHandle(handle, True)
      Else
         Throw New FileNotFoundException(String.Format("Cannot open '{0}'", filename))
      End If

      ' Get file size.
      bufferSize = GetFileSize(safeHandle, upperWord) 
      If bufferSize = INVALID_FILE_SIZE Then
         bufferSize = -1
      Else If upperWord > 0 Then 
         bufferSize = (CLng(upperWord) << 32) + bufferSize
      End If     
   End Sub

   Public ReadOnly Property Size As Long
      Get
         Return bufferSize
      End Get
   End Property

   Public Sub Dispose() _
              Implements IDisposable.Dispose
      Dispose(True)
      GC.SuppressFinalize(Me)
   End Sub           

   Protected Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Exit Sub

      ' Dispose of managed resources here.
      If disposing Then
         safeHandle.Dispose()
      End If

      ' Dispose of any unmanaged resources not wrapped in safe handles.

      disposed = True
   End Sub  
End Class
```

## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>使用安全控制代碼實作衍生類別的處置模式

下列範例將說明衍生類別 `DisposableStreamResource2` 的處置模式，該類別繼承自上述範例中顯示的 `DisposableStreamResource` 類別。 這個類別會新增額外的方法 `WriteFileInfo`，並使用 [SafeFileHandle](xref:Microsoft.Win32.SafeHandles.SafeFileHandle) 物件包裝可寫入檔案的控制代碼。 

```cs
using Microsoft.Win32.SafeHandles;
using System;
using System.IO;
using System.Runtime.InteropServices;
using System.Threading;

public class DisposableStreamResource2 : DisposableStreamResource
{
   // Define additional constants.
   protected const uint GENERIC_WRITE = 0x40000000; 
   protected const uint OPEN_ALWAYS = 4;

   // Define additional APIs.
   [DllImport("kernel32.dll")]   
   protected static extern bool WriteFile(
                                SafeFileHandle safeHandle, string lpBuffer, 
                                int nNumberOfBytesToWrite, out int lpNumberOfBytesWritten,
                                IntPtr lpOverlapped);

   // Define locals.
   private bool disposed = false;
   private string filename;
   private bool created = false;
   private SafeFileHandle safeHandle;

   public DisposableStreamResource2(string filename) : base(filename)
   {
      this.filename = filename;
   }

   public void WriteFileInfo()
   { 
      if (! created) {
         IntPtr hFile = CreateFile(xref:".\FileInfo.txt", GENERIC_WRITE, 0, 
                                   IntPtr.Zero, OPEN_ALWAYS, 
                                   FILE_ATTRIBUTE_NORMAL, IntPtr.Zero);
         if (hFile != INVALID_HANDLE_VALUE)
            safeHandle = new SafeFileHandle(hFile, true);
         else
            throw new IOException("Unable to create output file.");

         created = true;
      }

      string output = String.Format("{0}: {1:N0} bytes\n", filename, Size);
      int bytesWritten;
      bool result = WriteFile(safeHandle, output, output.Length, out bytesWritten, IntPtr.Zero);                                     
   }

   protected new virtual void Dispose(bool disposing)
   {
      if (disposed) return;

      // Release any managed resources here.
      if (disposing)
         safeHandle.Dispose();

      disposed = true;

      // Release any unmanaged resources not wrapped by safe handles here.

      // Call the base class implementation.
      base.Dispose(true);
   }
}
```

```vb
Imports Microsoft.Win32.SafeHandles
Imports System.IO

Public Class DisposableStreamResource2 : Inherits DisposableStreamResource
   ' Define additional constants.
   Protected Const GENERIC_WRITE As Integer = &H40000000 
   Protected Const OPEN_ALWAYS As Integer = 4

   ' Define additional APIs.
   Protected Declare Function WriteFile Lib "kernel32.dll" (
                              safeHandle As SafeFileHandle, lpBuffer As String, 
                              nNumberOfBytesToWrite As Integer, ByRef lpNumberOfBytesWritten As Integer,
                              lpOverlapped As Object) As Boolean

   ' Define locals.
   Private disposed As Boolean = False
   Private filename As String
   Private created As Boolean = False
   Private safeHandle As SafeFileHandle

   Public Sub New(filename As String)
      MyBase.New(filename)
      Me.filename = filename
   End Sub

   Public Sub WriteFileInfo() 
      If Not created Then
         Dim hFile As IntPtr = CreateFile(".\FileInfo.txt", GENERIC_WRITE, 0, 
                                          IntPtr.Zero, OPEN_ALWAYS, 
                                          FILE_ATTRIBUTE_NORMAL, IntPtr.Zero)
         If hFile <> INVALID_HANDLE_VALUE Then
            safeHandle = New SafeFileHandle(hFile, True)
         Else
            Throw New IOException("Unable to create output file.")
         End If
         created = True
      End If
      Dim output As String = String.Format("{0}: {1:N0} bytes {2}", filename, Size, 
                                           vbCrLf)
      WriteFile(safeHandle, output, output.Length, 0&, Nothing)                                     
   End Sub

   Protected Overloads Overridable Sub Dispose(disposing As Boolean)
      If disposed Then Exit Sub

      ' Release any managed resources here.
      If disposing Then
         safeHandle.Dispose()
      End If

      disposed = True
      ' Release any unmanaged resources not wrapped by safe handles here.

      ' Call the base class implementation.
      MyBase.Dispose(True)
   End Sub
End Class
```

## <a name="see-also"></a>請參閱

[SuppressFinalize](xref:System.GC.SuppressFinalize(System.Object))

[IDisposable](xref:System.IDisposable)

[IDisposable.Dispose](xref:System.IDisposable.Dispose)

[Microsoft.Win32.SafeHandles](xref:Microsoft.Win32.SafeHandles)

[System.Runtime.InteropServices.SafeHandle](xref:System.Runtime.InteropServices.SafeHandle)

[IDisposable.Dispose](xref:System.IDisposable.Dispose)



<!--HONumber=Nov16_HO3-->


