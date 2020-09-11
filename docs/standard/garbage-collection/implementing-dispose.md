---
title: 實作 Dispose 方法
description: 在本文中，您將瞭解如何執行 Dispose 方法，以釋放您的程式碼在 .NET 中使用的非受控資源。
ms.date: 09/08/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- garbage collection, Dispose method
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
ms.openlocfilehash: 863f78daf13ae9d795c37c1c6f428d387b9a026b
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022918"
---
# <a name="implement-a-dispose-method"></a>實作 Dispose 方法

執行 <xref:System.IDisposable.Dispose%2A> 方法主要是用來釋放非受控資源。 使用實作為實作為的實例成員時 <xref:System.IDisposable> ，通常會發生 cascade <xref:System.IDisposable.Dispose%2A> 呼叫。 有其他原因需要執行 <xref:System.IDisposable.Dispose%2A> ，例如若要釋放已配置的記憶體，請移除已加入至集合的專案，或發出已取得之鎖定的版本。

[.Net 垃圾收集](index.md)行程不會配置或釋放非受控記憶體。 處置物件的模式稱為處置模式，會在物件的存留期上強加順序。 處置模式用於執行介面的物件 <xref:System.IDisposable> ，而且在與檔案和管道控制碼、登錄控制碼、等候控制碼或非受控記憶體的指標指標互動時很常見。 這是因為垃圾收集行程無法回收未受管理的物件。

為了協助確保資源一律會適當地清除， <xref:System.IDisposable.Dispose%2A> 方法應該具有等冪性，使其可在不擲回例外狀況的情況下呼叫多次。 此外，的後續調用 <xref:System.IDisposable.Dispose%2A> 也不應該執行任何動作。

針對此方法提供的程式碼範例會 <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> 顯示垃圾收集如何造成完成項的執行，而物件或其成員的非受控參考仍在使用中。 利用 <xref:System.GC.KeepAlive%2A?displayProperty=nameWithType> 來讓物件不符合從目前常式開始到呼叫這個方法的時間點的垃圾收集，是合理的。

## <a name="safe-handles"></a>安全控制碼

撰寫物件完成項的程式碼是一項複雜的工作，若未正確撰寫，可能會造成問題。 因此，建議您建構 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> 物件，而不要實作完成項。

是一種 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> 抽象的 managed 型別，可包裝 <xref:System.IntPtr?displayProperty=nameWithType> 識別非受控資源的。 在 Windows 上，它可能會識別 Unix 上的控制碼，也就是檔案描述項。 它會提供所有必要的邏輯，以確保此資源只會釋出一次，而當 `SafeHandle` 處置或的所有參考都已卸載， `SafeHandle` 且 `SafeHandle` 實例已完成時。

<xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>是抽象基類。 衍生類別提供不同類型之控制碼的特定實例。 這些衍生類別會驗證的值 <xref:System.IntPtr?displayProperty=nameWithType> 會被視為無效，以及實際釋放控制碼的方式。 例如， <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> 衍生自 `SafeHandle` 以包裝來 `IntPtrs` 識別開啟的檔案控制代碼/描述項，並覆寫其 <xref:System.Runtime.InteropServices.SafeHandle.ReleaseHandle?displayProperty=nameWithType> 方法，以透過 Unix 上的函式 `close` 或 Windows) 上的函式將其關閉 (`CloseHandle` 。 在 .NET 程式庫中建立非受控資源的大部分 Api 都會將其包裝在中， `SafeHandle` 並 `SafeHandle` 視需要傳回給您，而不是傳回原始指標。 在您與非受控元件互動並取得 `IntPtr` 非受控資源的情況下，您可以建立自己的 `SafeHandle` 型別來包裝。 因此，少數的非 `SafeHandle` 類型需要執行完成項; 大部分可處置的模式執行只會結束其他 managed 資源的包裝，其中某些可能是 `SafeHandle` 。

<xref:Microsoft.Win32.SafeHandles> 命名空間中的下列衍生類別會提供安全控制代碼：

- <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>、<xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle> 和 <xref:Microsoft.Win32.SafeHandles.SafePipeHandle> 類別，適用於檔案、記憶體對應檔案和管道。
- <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle> 類別，適用於記憶體檢視。
- <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>、<xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle> 和 <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle> 類別，適用於加密建構。
- <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle> 類別，適用於登錄機碼。
- <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle> 類別，適用於等候控制代碼。

## <a name="dispose-and-disposebool"></a>Dispose ( # A1 和 Dispose (bool) 

<xref:System.IDisposable> 介面要求實作單一無參數方法 <xref:System.IDisposable.Dispose%2A>。 此外，任何非密封類別都應該要執行額外的多載 `Dispose(bool)` 方法：

- 沒有 `public` `NonInheritable` 參數的 Visual Basic) 執行中的非虛擬 (<xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 。

- `protected virtual`Visual Basic) 方法的 (，其簽章 `Overridable` `Dispose` 為：

  [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
  [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]

  > [!IMPORTANT]
  > `disposing`參數應該是 `false` 從完成項呼叫，並 `true` 從方法呼叫時 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 。 換句話說，它會在具 `true` 決定性的呼叫時，以及 `false` 不具決定性的呼叫時。

### <a name="the-dispose-method"></a>Dispose ( # A1 方法

因為 `public` Visual Basic) 中的非虛擬 (`NonInheritable` ，無參數 `Dispose` 方法是由型別的取用者呼叫，其目的是要釋放未受管理的資源、執行一般清除，以及指出完成項（如果有的話）不需要執行。 釋放與受管理物件相關聯的實際記憶體一律是 [垃圾收集](index.md)行程的網域。 因此，它擁有標準實作：

[!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
[!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]

`Dispose` 方法會執行所有物件清除，所以記憶體回收行程不需要再呼叫物件的 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 覆寫。 因此，呼叫 <xref:System.GC.SuppressFinalize%2A> 方法會防止記憶體回收行程執行完成項。 如果類型沒有完成項，則呼叫 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType> 沒有作用。 請注意，實際清除是由方法多載所執行 `Dispose(bool)` 。

### <a name="the-disposebool-method-overload"></a>Dispose (bool) 方法多載

在多載中， `disposing` 參數是 <xref:System.Boolean> ，指出方法呼叫 <xref:System.IDisposable.Dispose%2A> 是來自方法 (它的值是 `true`) 或從完成項 (其值 `false`) 。

方法的主體是由兩個程式碼區塊所構成：

- 釋放 Unmanaged 資源的區塊。 不論 `disposing` 參數的值為何，這個區塊都會執行。
- 釋放 Managed 資源的條件性區塊。 如果 `disposing` 的值為 `true`，這個區塊就會執行。 它所釋放的 Managed 資源可能包括：

  - **實作 <xref:System.IDisposable> 的受控物件。** 條件式區塊可以用來呼叫其 <xref:System.IDisposable.Dispose%2A> 實 (cascade dispose) 。 如果您使用的衍生類別 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> 來包裝未受管理的資源，您應該在 <xref:System.Runtime.InteropServices.SafeHandle.Dispose?displayProperty=nameWithType> 這裡呼叫執行。

  - **耗用大量記憶體或耗用少量資源的 Managed 物件。** 將大型的 managed 物件參考指派給， `null` 使其更容易無法連接。 這會比以非決定性的方式來釋出它們，而這通常是在條件式區塊之外進行。

如果方法呼叫來自完成項，則只應執行釋出非受控資源的程式碼。 實施者負責確保 false 路徑不會與可能已回收的 managed 物件互動。 這點很重要，因為垃圾收集行程在完成期間終結 managed 物件的順序不具決定性。

## <a name="cascade-dispose-calls"></a>Cascade dispose 呼叫

如果您的類別擁有欄位或屬性，且其型別為實 <xref:System.IDisposable> ，則包含類別本身也應該會執行 <xref:System.IDisposable> 。 具 <xref:System.IDisposable> 現化實作為實例成員並將其儲存為實例成員的類別，也會負責其清除。 這是為了協助確保參考的可處置型別有機會透過方法明確地執行清除 <xref:System.IDisposable.Dispose%2A> 。 在此範例中，類別是 `sealed` `NotInheritable` 在 Visual Basic) 中 (或。

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/disposable1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/disposable1.vb#1)]

## <a name="implement-the-dispose-pattern"></a>執行處置模式

所有非密封類別或 (Visual Basic 類別未修改為 `NotInheritable`) 應該被視為可能的基類，因為它們可以被繼承。 如果您針對任何可能的基類執行處置模式，則必須提供下列各項：

- 呼叫 <xref:System.IDisposable.Dispose%2A> 方法的 `Dispose(bool)` 實作。
- `Dispose(bool)`執行實際清除的方法。
- 衍生自包裝您的 Unmanaged 資源之 <xref:System.Runtime.InteropServices.SafeHandle> 的類別 (建議使用)，或式 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法的覆寫。 <xref:System.Runtime.InteropServices.SafeHandle>類別會提供完成項，因此您不需要自行撰寫。

> [!IMPORTANT]
> 基類可以只參考 managed 物件，並執行處置模式。 在這些情況下，不需要完成項。 只有當您直接參考未受管理的資源時，才需要完成項。

以下一般模式將會實作使用安全控制代碼之基底類別的處置模式。

[!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
[!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]

> [!NOTE]
> 上一個範例使用 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> 物件來說明模式；可改用任何衍生自 <xref:System.Runtime.InteropServices.SafeHandle> 的物件。 請注意，該範例未正確地執行個體化其 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> 物件。

以下一般模式將會實作覆寫 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 之基底類別的處置模式。

[!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
[!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]

> [!TIP]
> 在 c # 中，您可以 [藉由覆](../../csharp/programming-guide/classes-and-structs/destructors.md) 寫來建立完成項 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 。 在 Visual Basic 中，這是透過進行 `Protected Overrides Sub Finalize()` 。

## <a name="implement-the-dispose-pattern-for-a-derived-class"></a>執行衍生類別的處置模式

從實作 <xref:System.IDisposable> 介面的類別衍生的類別不應該實作 <xref:System.IDisposable>，因為 <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> 的基底類別實作會由其衍生類別繼承。 相反地，若要清除衍生類別，請提供下列各項：

- `protected override void Dispose(bool)`覆寫基類方法並執行衍生類別實際清除的方法。 這個方法也必須 `base.Dispose(bool)` `MyBase.Dispose(bool)` 在基類的 Visual Basic) 方法中呼叫 (，並將其處置狀態傳遞給引數。
- 衍生自包裝您的 Unmanaged 資源之 <xref:System.Runtime.InteropServices.SafeHandle> 的類別 (建議使用)，或式 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 方法的覆寫。 <xref:System.Runtime.InteropServices.SafeHandle> 類別會提供完成項，讓您不必自行撰寫程式碼。 如果您提供完成項，它必須 `Dispose(bool)` 使用的 `disposing` 引數來呼叫多載 `false` 。

以下一般模式將會實作使用安全控制代碼之衍生類別的處置模式：

[!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
[!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]

> [!NOTE]
> 上一個範例使用 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> 物件來說明模式；可改用任何衍生自 <xref:System.Runtime.InteropServices.SafeHandle> 的物件。 請注意，該範例未正確地執行個體化其 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> 物件。

以下一般模式將會實作覆寫 <xref:System.Object.Finalize%2A?displayProperty=nameWithType> 之衍生類別的處置模式：

[!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
[!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]

## <a name="implement-the-dispose-pattern-with-safe-handles"></a>使用安全控制碼來執行處置模式

下列範例將說明使用安全控制代碼封裝 Unmanaged 資源之基底類別 `DisposableStreamResource` 的處置模式。 它會定義 `DisposableStreamResource` 類別，該類別使用 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> 包裝代表開啟檔案的 <xref:System.IO.Stream> 物件。 此類別也包含單一屬性，這個屬性會傳回檔案 `Size` 資料流程中的總位元組數。

[!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
[!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]

## <a name="implement-the-dispose-pattern-for-a-derived-class-with-safe-handles"></a>使用安全控制碼來執行衍生類別的處置模式

下列範例將說明衍生類別 `DisposableStreamResource2` 的處置模式，該類別繼承自上述範例中顯示的 `DisposableStreamResource` 類別。 這個類別會加入額外的方法 `WriteFileInfo`，並使用 <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> 物件包裝可寫入檔案的控制代碼。

[!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
[!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]

## <a name="see-also"></a>另請參閱

- <xref:System.GC.SuppressFinalize%2A>
- <xref:System.IDisposable>
- <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>
- <xref:Microsoft.Win32.SafeHandles>
- <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType>
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>
- [定義和使用類別和結構 (c + +/CLI) ](/cpp/dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli)
