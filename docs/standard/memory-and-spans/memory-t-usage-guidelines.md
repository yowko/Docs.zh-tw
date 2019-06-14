---
title: Memory<T> 與 Span<T> 使用指導方針
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 380c0eef137eb5142c30e63f5446f5d60723087a
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2019
ms.locfileid: "66834049"
---
# <a name="memoryt-and-spant-usage-guidelines"></a>Memory\<T> 與 Span\<T> 使用指導方針

.NET Core 包含數個可代表記憶體任意連續區域的類型。 .NET Core 2.0 已導入 <xref:System.Span%601> 和 <xref:System.ReadOnlySpan%601>，其為可由受控或非受控記憶體所支援的輕量型記憶體緩衝區。 由於這些類型可以儲存在堆疊上，使得它們很適合用於包含非同步方法呼叫在內的數種案例。 .NET Core 2.1 新增數個額外類型，包括 <xref:System.Memory%601>、<xref:System.ReadOnlyMemory%601>、<xref:System.Buffers.IMemoryOwner%601>，以及 <xref:System.Buffers.MemoryPool%601>。 <xref:System.Memory%601> 和其相關類型與 <xref:System.Span%601> 類似，可以由受控和非受控記憶體支援。 <xref:System.Memory%601> 與 <xref:System.Span%601> 不同，只能儲存在受控堆積上。

<xref:System.Span%601> 和 <xref:System.Memory%601> 都是可用於管線中的結構化資料緩衝區。 也就是說，它們是被設計成能使部分或所有資料都能有效率地被傳遞至管線中的元件，其可處理它們或選擇性地修改緩衝區。 由於 <xref:System.Memory%601> 和其相關類型皆可由多個元件或多個執行緒存取，開發人員必須遵循一些標準的使用指導方針，以產生強固的程式碼。

## <a name="owners-consumers-and-lifetime-management"></a>擁有者、取用者及存留期管理

由於緩衝區可在 API 之間傳遞，且緩衝區有時可以從多個執行緒存取，因此考慮存留期管理是一件非常重要的工作。 有三個核心概念：

- **擁有權**。 緩衝區執行個體的擁有者必須負責處理存留期管理，其中包括終結不再使用的緩衝區。 所有緩衝區都具有單一擁有者。 擁有者通常是建立緩衝區，或是從處理站接收緩衝區的元件。 擁有權也可以被轉移；**元件 A** 可以將緩衝區的控制轉移給**元件 B**，這會使**元件 A** 無法繼續使用該緩衝區，且**元件 B** 需負責在該緩衝區不再使用時終結它。

- **使用情況**。 緩衝區執行個體的取用者可以透過從緩衝區執行個體進行讀取，或在某些情況下對它進行寫入，來使用該緩衝區執行個體。 緩衝區一次可以有一個取用者，除非已提供某種外部同步處理機制。 請注意，作用中的緩衝區取用者並不一定是該緩衝區的擁有者。

- **租用**。 租用是特定元件可作為緩衝區取用者的時間長度。

下列虛擬程式碼範例會說明這三個概念。 它包含能具現化 <xref:System.Char> 類型之 <xref:System.Memory%601> 緩衝區的 `Main` 方法，呼叫 `WriteInt32ToBuffer` 方法以將某個整數的字串表示法寫入該緩衝區，然後呼叫 `DisplayBufferToConsole` 方法來顯示該緩衝區的值。

```csharp
using System;

class Program
{
    // Write 'value' as a human-readable string to the output buffer.
    void WriteInt32ToBuffer(int value, Buffer buffer);

    // Display the contents of the buffer to the console.
    void DisplayBufferToConsole(Buffer buffer);

    // Application code
    static void Main()
    {
        var buffer = CreateBuffer();
        try
        {
            int value = Int32.Parse(Console.ReadLine());
            WriteInt32ToBuffer(value, buffer);
            DisplayBufferToConsole(buffer);
        }
        finally
        {
            buffer.Destroy();
        }
    }
}
```

`Main` 方法會建立緩衝區 (在此範例中為 <xref:System.Span%601> 執行個體)，因此為其擁有者。 因此，`Main` 必須負責在該緩衝區不再使用時終結它。 它會透過呼叫緩衝區的 <xref:System.Span%601.Clear?displayProperty=nameWithType> 方法來執行此動作。 (這裡的 <xref:System.Span%601.Clear> 方法實際上會清除緩衝區的記憶體，<xref:System.Span%601> 結構實際上沒有能終結緩衝區的方法)。

該緩衝區具有兩個取用者，`WriteInt32ToBuffer` 和 `DisplayBufferToConsole`。 一次只會有一個取用者 (先是 `WriteInt32ToBuffer`，然後是 `DisplayBufferToConsole`)，且這兩個取用者都不是該緩衝區的擁有者。 請注意，「取用者」一詞在此內容中並不代表針對緩衝區的唯讀檢視；如果將緩衝區的讀取/寫入檢視授與取用者，其將能修改緩衝區的內容 (如此範例中的 `WriteInt32ToBuffer`)。

`WriteInt32ToBuffer` 方法在介於方法呼叫和方法傳回之間的時間內，針對該緩衝區會具有租用 (可取用該緩衝區)。 同樣地，在緩衝區執行期間，`DisplayBufferToConsole` 針對該緩衝區會具有租用，而該租用會在該方法回朔時釋放。 (沒有適用於租用管理的 API，「租用」本身是一種概念)。

## <a name="memoryt-and-the-ownerconsumer-model"></a>Memory\<T> 和擁有者/取用者模型

如同[擁有者、取用者及存留期管理](#owners-consumers-and-lifetime-management)一節所述，緩衝區一律會有一個擁有者。 .NET Core 支援兩種擁有權模型：

- 支援單一擁有權的模型。 緩衝區在其存留期的整個期間，都會有單一的擁有者。

- 支援擁有權傳輸的模型。 緩衝區的擁有權可以從其原始擁有者 (其建立者) 轉換到另一個元件，而該元件將會接手負責該緩衝區的存留期管理。 該擁有者接著可以再次將擁有權轉換到又另一個元件，依此類推。

您會使用 <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> 介面來明確管理緩衝區的擁有權。 <xref:System.Buffers.IMemoryOwner%601> 同時支援這兩種擁有權模型。 具有 <xref:System.Buffers.IMemoryOwner%601> 參考的元件會擁有緩衝區。 下列範例會使用 <xref:System.Buffers.IMemoryOwner%601?> 執行個體來反映 <xref:System.Memory%601> 緩衝區的擁有權。

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

我們也可以搭配 [`using`](~/docs/csharp/language-reference/keywords/using-statement.md) 來撰寫此範例：

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

在此程式碼中：

- `Main` 方法會保留針對 <xref:System.Buffers.IMemoryOwner%601> 執行個體的參考，因此 `Main` 方法是該緩衝區的擁有者。

- `WriteInt32ToBuffer` 和 `DisplayBufferToConsole` 方法接受 <xref:System.Memory%601> 作為公用 API。 因此，它們是該緩衝區的取用者。 且它們之間一次只有一個會取用緩衝區。

雖然 `WriteInt32ToBuffer` 方法的目的是要將值寫入緩衝區，但 `DisplayBufferToConsole` 方法則不會這麼做。 為了反映此情況，它可以接受 <xref:System.ReadOnlyMemory%601>類型的引數。 如需 <xref:System.ReadOnlyMemory%601> 的詳細資訊，請參閱[規則 #2：在緩衝區必須是唯讀的情況下使用 ReadOnlySpan\<T> 或 ReadOnlyMemory\<T>](#rule-2)。

### <a name="ownerless-memoryt-instances"></a>「無擁有者」的 Memory\<T> 執行個體

您可以在不使用 <xref:System.Buffers.IMemoryOwner%601> 的情況下建立 <xref:System.Memory%601> 執行個體。 在此情況下，緩衝區的擁有權是隱含而非明確的，且僅支援單一擁有者模型。 您可以這麼做來達到此目的：

- 直接呼叫其中一個 <xref:System.Memory%601> 建構函式並傳遞 `T[]`，如下列範例所示。

- 呼叫 [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) 擴充方法來產生 `ReadOnlyMemory<char>` 執行個體。

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

一開始建立 <xref:System.Memory%601> 執行個體的方法，便是緩衝區的隱含擁有者。 擁有權並無法被轉移到任何其他元件，因為沒有 <xref:System.Buffers.IMemoryOwner%601> 執行個體來促成該轉移。 (或者，您也可以想像執行階段的記憶體回收行程擁有該緩衝區，而所有方法皆只是取用該緩衝區)。

## <a name="usage-guidelines"></a>使用指導方針

由於記憶體區塊具有擁有者，同時會被傳遞至多個元件，且某些元件則會在特定的記憶體區塊上運作，因此有必要針對 <xref:System.Memory%601> 和 <xref:System.Span%601> 的使用建立指導方針。  指導方針之所以必要，是因為：

- 元件可能會在記憶體區塊的擁有者釋放它之後，保留針對該記憶體區塊的參考。

- 元件可能會和另一個元件同時在緩衝區上運作，並在期間損毀緩衝區中的資料。

- 雖然 <xref:System.Span%601> 的堆疊配置特性能對效能進行最佳化，並使 <xref:System.Span%601> 成為在記憶體區塊上運作的偏好類型，但它也會使 <xref:System.Span%601> 受制於某些顯著限制。 請務必了解 <xref:System.Span%601> 和 <xref:System.Memory%601>的個別使用時機。

下列為針對順利使用 <xref:System.Memory%601> 和其相關類型的建議。 請注意，除非我們明確提及，否則適用於 <xref:System.Memory%601> 和 <xref:System.Span%601> 的指引，同時也會適用於 <xref:System.ReadOnlyMemory%601> 和 <xref:System.ReadOnlySpan%601>。

**規則 #1：針對同步 API，在可能的情況下，請使用 Span\<T> 而非 Memory\<T> 作為參數。**

<xref:System.Span%601> 比起 <xref:System.Memory%601> 更為靈活，且可以代表較廣泛類型的連續記憶體緩衝區。 <xref:System.Span%601> 也能夠提供比 <xref:System.Memory%601> 更為優異的效能。 最後，雖然 Span\<T> 並無法轉換為 Memory\<T>，您可以使用 <xref:System.Memory%601.Span?displayProperty=nameWithType> 屬性來將 <xref:System.Memory%601> 執行個體轉換為 <xref:System.Span%601>。 因此如果您的呼叫端具有 <xref:System.Memory%601> 執行個體，它們仍然可以搭配 <xref:System.Span%601> 參數來呼叫您的方法。

使用 <xref:System.Span%601> 類型 (而非 <xref:System.Memory%601> 類型) 的參數也可以協助您寫入到正確的使用方法實作。 您將能自動取得編譯時間檢查，以確保您不會嘗試在方法租用以外的時間嘗試存取緩衝區 (將於稍後詳述)。

有時候，您將必須使用 <xref:System.Memory%601> 參數來取代 <xref:System.Span%601> 參數，就算您是完全同步也一樣。 也許您仰賴的某個 API 僅接受 <xref:System.Memory%601> 引數。 這並沒有關係，但您必須記得以同步處理方式使用 <xref:System.Memory%601> 所會帶來的取捨。

<a name="rule-2" />

**規則 #2：在緩衝區必須是唯讀的情況下使用 ReadOnlySpan\<T> 或 ReadOnlyMemory\<T>。**

在稍早的範例中，`DisplayBufferToConsole` 方法只會從緩衝區讀取，它並不會修改緩衝區的內容。 方法簽章應變更為下列項目。

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

事實上，如果我們將此規則與規則 #1 結合，我們便能進一步將方法簽章重新撰寫為下列項目：

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

`DisplayBufferToConsole` 方法現在能與幾乎所有已知的緩衝區類型搭配運作：`T[]`、搭配 [stackalloc](~/docs/csharp/language-reference/operators/stackalloc.md) 配置的儲存體等。 您甚至可以直接將 <xref:System.String> 傳遞給它！

**規則 #3：如果您的方法接受 Memory\<T> 並會傳回 `void`，您不能在方法傳回時使用 Memory\<T> 執行個體。**

這與稍早提及的「租用」相關。 會傳回 void 的方法針對 <xref:System.Memory%601> 執行個體的租用，會在該方法進入時開始，並在方法離開時結束。 請參考下列範例，其會根據來自主控台的輸入，以迴圈方式呼叫 `Log`。

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

如果 `Log` 是完全同步的方法，此程式碼會依預期的方式運作，因為記憶體執行個體在任何時候皆只有一個作用中的取用者。
但想像 `Log` 具有此實作的情況。

```csharp
// !!! INCORRECT IMPLEMENTATION !!!
static void Log(ReadOnlyMemory<char> message)
{
    // Run in background so that we don't block the main thread while performing IO.
    Task.Run(() =>
    {
        StreamWriter sw = File.AppendText(@".\input-numbers.dat");
        sw.WriteLine(message);
    });
}
```

在此實作中，`Log` 會違反其租用，因為在原始方法已傳回之後，它仍然會於背景嘗試使用 <xref:System.Memory%601> 執行個體。 在 `Log` 嘗試從緩衝區讀取時，`Main` 方法可能會對緩衝區造成變動，並進一步導致資料損毀。

有幾個方式可以解決此情況：

- `Log` 方法可以傳回 <xref:System.Threading.Tasks.Task> 而非 `void`，如下列 `Log` 方法的實作所示。

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- 可以改為以下列方式實作 `Log`：

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

**規則 #4：如果您的記憶體接受 Memory\<T> 並會傳回 Task，您不能在 Task 轉換為終止狀態之後使用 Memory\<T> 執行個體。**

這基本上是規則 #3 的非同步變化。 先前範例的 `Log` 方法可以透過下列方式撰寫來符合此規則：

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

在這裡，「終止狀態」表示工作已轉換為已完成、已發生錯誤，或已取消的狀態。 換句話說，「終止狀態」的意思是「任何會導致等候擲回或繼續執行的項目」。

此指南適用於會傳回 <xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601>、<xref:System.Threading.Tasks.ValueTask%601>，或任何類似類型的方法。

**規則 #5：如果您的建構函式接受 Memory\<T> 作為參數，已建構物件上的執行個體方法將會被假設為 Memory\<T> 執行個體的取用者。**

參考下列範例：

```csharp
class OddValueExtractor
{
    public OddValueExtractor(ReadOnlyMemory<int> input);
    public bool TryReadNextOddValue(out int value);
}

void PrintAllOddValues(ReadOnlyMemory<int> input)
{
    var extractor = new OddValueExtractor(input);
    while (extractor.TryReadNextOddValue(out int value))
    {
      Console.WriteLine(value);
    }
}
```

在這裡，`OddValueExtractor` 建構函式會接受 `ReadOnlyMemory<int>` 作為建構函式參數，因此建構函式本身是 `ReadOnlyMemory<int>` 執行個體的取用者，且已傳回值上的所有執行個體方法也都會是原始 `ReadOnlyMemory<int>` 執行個體的取用者。 這代表 `TryReadNextOddValue` 會取用 `ReadOnlyMemory<int>` 執行個體，就算該執行個體不會直接被傳遞至 `TryReadNextOddValue` 方法也一樣。

**規則 #6：如果您的類型上具有可設定的 Memory\<T> 類型屬性 (或是對等的執行個體方法)，該物件上的執行個體方法都會被假設為 Memory\<T> 執行個體的取用者。**

這基本上是規則 #5 的變化。 此規則之所以存在，是因為我們會假設屬性設定者或對等方法會擷取或保留其輸入，好讓相同物件上的執行個體方法能夠運用擷取的狀態。

下列範例會觸發此規則：

```csharp
class Person
{
    // Settable property.
    public Memory<char> FirstName { get; set; }

    // alternatively, equivalent "setter" method
    public SetFirstName(Memory<char> value);

    // alternatively, a public settable field
    public Memory<char> FirstName;
}
```

**規則 #7：如果您有 IMemoryOwner\<T> 參考，您必須在某個時間點處置它或轉換其擁有權 (但不能兩者皆執行)。**

由於 <xref:System.Memory%601> 執行個體可由受控或非受控記憶體支援，擁有者必須在 <xref:System.Memory%601> 執行個體上的作業完成時呼叫 <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>。 或者，擁有者可以將 <xref:System.Buffers.IMemoryOwner%601> 執行個體的擁有權轉換給不同的元件，而在轉換之後，取得擁有權的元件便必須負責在適當的時機呼叫 <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> (將於稍後詳述)。

若未呼叫 <xref:System.Buffers.MemoryPool%601.Dispose%2A> 方法，可能會導致非受控的記憶體流失或其他效能降低。

此規則也適用於呼叫 Factory 方法 (例如 <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>) 的程式碼。 呼叫者會成為傳回 <xref:System.Buffers.IMemoryOwner%601> 的擁有者，並須負責在完成時處置執行個體。

**規則 #8：如果您的 API 介面中具有 IMemoryOwner\<T> 參數，便代表您接受該執行個體的擁有權。**

接受此類型的執行個體，便代表您的元件意圖取得此執行個體的擁有權。 您的元件必須負責進行規則 #7 中所述的適當處置。

將 <xref:System.Buffers.IMemoryOwner%601> 執行個體的擁有權轉換給另一個元件的任何元件，都不應該在方法呼叫完成之後繼續使用該執行個體。

> [!IMPORTANT]
> 如果您的建構函式會接受 <xref:System.Buffers.IMemoryOwner%601> 作為參數，其類型應實作 <xref:System.IDisposable>，且您的 <xref:System.IDisposable.Dispose%2A> 方法應該要呼叫 <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>。

**規則 #9：如果您正在包裝同步的 p/invoke 方法，您的 API 應該接受 Span\<T> 作為參數。**

根據規則 #1，<xref:System.Span%601> 通常是應該用於同步 API 的正確類型。 您可以透過 [`fixed`](~/docs/csharp/language-reference/keywords/fixed-statement.md) 關鍵字釘選 <xref:System.Span%601> 執行個體，如下列範例所示。

```csharp
using System.Runtime.InteropServices;

[DllImport(...)]
private static extern unsafe int ExportedMethod(byte* pbData, int cbData);

public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        int retVal = ExportedMethod(pbData, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

在先前的範例中，`pbData` 在如輸入 span 為空白之類的情況下，可能會是 Null。 如果匯出的方法一定需要 `pbData` 是非 Null (就算 `cbData` 是 0)，則可以如下所示實作該方法：

```csharp
public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        byte dummy = 0;
        int retVal = ExportedMethod((pbData != null) ? pbData : &dummy, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

**規則 #10：如果您正在包裝非同步的 p/invoke 方法，您的 API 應該接受 Memory\<T> 作為參數。**

由於您無法在非同步作業上使用 [`fixed`](~/docs/csharp/language-reference/keywords/fixed-statement.md) 關鍵字，您會使用 <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> 方法來釘選 <xref:System.Memory%601> 執行個體，無論該執行個體所代表的連續記憶體類型為何。 下列範例示範如何使用此 API 來執行非同步 p/invoke 呼叫。

```csharp
using System.Runtime.InteropServices;

[UnmanagedFunctionPointer(...)]
private delegate void OnCompletedCallback(IntPtr state, int result);

[DllImport(...)]
private static extern unsafe int ExportedAsyncMethod(byte* pbData, int cbData, IntPtr pState, IntPtr lpfnOnCompletedCallback);

private static readonly IntPtr _callbackPtr = GetCompletionCallbackPointer();

public unsafe Task<int> ManagedWrapperAsync(Memory<byte> data)
{
    // setup
    var tcs = new TaskCompletionSource<int>();
    var state = new MyCompletedCallbackState
    {
        Tcs = tcs
    };
    var pState = (IntPtr)GCHandle.Alloc(state);

    var memoryHandle = data.Pin();
    state.MemoryHandle = memoryHandle;

    // make the call
    int result;
    try
    {
        result = ExportedAsyncMethod((byte*)memoryHandle.Pointer, data.Length, pState, _callbackPtr);
    }
    catch
    {
        ((GCHandle)pState).Free(); // cleanup since callback won't be invoked
        memoryHandle.Dispose();
        throw;
    }

    if (result != PENDING)
    {
        // Operation completed synchronously; invoke callback manually
        // for result processing and cleanup.
        MyCompletedCallbackImplementation(pState, result);
    }

    return tcs.Task;
}

private static void MyCompletedCallbackImplementation(IntPtr state, int result)
{
    GCHandle handle = (GCHandle)state;
    var actualState = (MyCompletedCallbackState)state;
    handle.Free();
    actualState.MemoryHandle.Dispose();

    /* error checking result goes here */

    if (error)
    {
        actualState.Tcs.SetException(...);
    }
    else
    {
        actualState.Tcs.SetResult(result);
    }
}

private static IntPtr GetCompletionCallbackPointer()
{
    OnCompletedCallback callback = MyCompletedCallbackImplementation;
    GCHandle.Alloc(callback); // keep alive for lifetime of application
    return Marshal.GetFunctionPointerForDelegate(callback);
}

private class MyCompletedCallbackState
{
    public TaskCompletionSource<int> Tcs;
    public MemoryHandle MemoryHandle;
}
```

## <a name="see-also"></a>另請參閱

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
