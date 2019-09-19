---
title: 將您的 Windows 市集應用程式移轉至 .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fdff7aa92e4c1c357c83b625a6daadbf0a8d556b
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049521"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a>將您的 Windows 市集應用程式移轉至 .NET Native

.NET Native 在 Windows Store 或開發人員的電腦上提供應用程式的靜態編譯。 這不同於 just-in-time (JIT) 編譯器或裝置上的 [原生映像產生器 (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) 為 Windows 市集應用程式執行的動態編譯。 儘管有差異, .NET Native 會嘗試維持與適用于[Windows Store 應用程式的 .net](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)的相容性。 在大部分的情況下, 適用于 Windows Store 應用程式的 .NET 的專案也會使用 .NET Native。  不過，在某些情況下，您可能會遇到行為上的變更。 本檔討論適用于 Windows Store 應用程式的標準 .NET 與下列領域的 .NET Native 之間的差異:

- [一般執行階段的差異](#Runtime)

- [動態程式設計的差異](#Dynamic)

- [其他與反映相關的差異](#Reflection)

- [不支援的案例和 API](#Unsupported)

- [Visual Studio 的差異](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a>一般執行階段的差異

- 當應用程式在<xref:System.TypeLoadException>common language runtime (CLR) 上執行時, JIT 編譯程式所擲回的例外狀況, 通常會在 .NET Native 處理時導致編譯時期錯誤。

- 請勿從應用程式的 UI 執行緒呼叫 <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> 方法。 這可能會導致 .NET Native 上發生鎖死。

- 請不要依賴靜態類別建構函式引動過程順序。 在 .NET Native 中, 調用順序與標準執行時間上的順序不同。 (即使是使用標準執行階段，也不應該依賴靜態類別建構函式的執行順序。)

- 在任何執行緒上無限迴圈，而不進行呼叫 (例如 `while(true);`) 可能會導致應用程式中止。 同樣地，長時間或無限等待可能也會導致應用程式中止。

- 某些一般初始化迴圈不會在 .NET Native 中擲回例外狀況。 例如，下列程式碼會在標準 CLR 上擲回 <xref:System.TypeLoadException> 例外狀況。 在 .NET Native 中, 它並不是。

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- 在某些情況下, .NET Native 會提供不同的 .NET Framework 類別庫的執行。 從方法傳回的物件一律會實作傳回類型的成員。 不過，由於其支援實作不同，所以您可能無法將其轉換成像在其他 .NET Framework 平台上轉換的相同類型集。 例如，在某些情況下，您可能無法將 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> 這類方法傳回的 <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> 介面物件轉換成 `T[]`。

- Windows Store 應用程式的 .NET 預設不會啟用 WinInet 快取, 但它是在 .NET Native 上。 這可以改善效能，但有工作集含意。 開發人員不需任何動作。

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a>動態程式設計的差異

.NET Native 從 .NET Framework 的程式碼中以靜態方式連結, 以將程式碼應用程式設為本機, 以達到最大效能。 不過，二進位大小必須維持在較小的狀態，這樣才不會將整個 .NET Framework 帶進來。 .NET Native 編譯器會使用移除未使用程式碼參考的相依性歸納器來解決這項限制。 不過, .NET Native 可能無法在編譯時期以靜態方式推斷資訊時, 維護或產生某些類型資訊和程式碼, 而是在執行時間動態地抓取。

.NET Native 會啟用反映和動態程式設計。 不過，並非所有類型都可以標記來進行反映，因為這樣會使所產生的程式碼大小過大 (尤其是因為可支援在 .NET Framework 中的公用 API 上反映)。 .NET Native 編譯器會對哪些類型應該支援反映進行智慧型選擇, 而且它會保留中繼資料, 而且只會針對那些類型產生程式碼。

例如，資料繫結會要求應用程式能夠將屬性名稱對應至函式。 在適用於 Windows 市集應用程式的 .NET 中，通用語言執行平台會自動使用反映來提供這項功能給 Managed 類型和可公開取得的原生類型。 在 .NET Native 中, 編譯器會自動包含您要系結資料之類型的中繼資料。

.NET Native 編譯器也可以處理常用的泛型型別 (例如<xref:System.Collections.Generic.List%601>和<xref:System.Collections.Generic.Dictionary%602>), 而不需要任何提示或指示詞。 在某些限制下，也可支援 [動態](../../csharp/language-reference/keywords/dynamic.md) 關鍵字。

> [!NOTE]
> 將應用程式移植到 .NET Native 時, 您應該徹底測試所有動態程式碼路徑。

.NET Native 的預設設定對大部分的開發人員而言已經足夠, 但有些開發人員可能會想要使用執行時間指示詞 (.) 來微調其設定。 此外, 在某些情況下, .NET Native 編譯器無法判斷哪些中繼資料必須可用於反映, 並依賴提示, 特別是在下列情況下:

- 無法以靜態方式判斷某些結構，例如 <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> 和 <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> 。

- 由於編譯器無法判斷具現化，所以必須以執行階段指示詞來指定您想要反映的泛型類型。 這不只是因為所有的程式碼必須包含在內，也因為反映在泛型類型上會形成無限循環 (例如，在泛型類型上叫用泛型方法時)。

> [!NOTE]
> 執行階段指示詞中定義在執行階段指示詞 (.rd.xml) 檔案中。 如需使用此檔案的一般資訊，請參閱[使用者入門](getting-started-with-net-native.md)。 如需執行階段指示詞的詳細資訊，請參閱 [Runtime Directives (rd.xml) Configuration File Reference](runtime-directives-rd-xml-configuration-file-reference.md)。

.NET Native 也包含程式碼剖析工具, 可協助開發人員判斷預設集合以外的哪些類型應該支援反映。

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a>其他與反映相關的差異

在適用于 Windows Store 應用程式的 .NET 與 .NET Native 之間, 有一些其他個別反映相關的行為差異。

在 .NET Native:

- 不支援 .NET Framework 類別庫中，透過類型和成員的私用反映。 不過，您可以透過自己的私用類型和成員，以及協力廠商程式庫中的類型和成員來進行反映。

- <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> 屬性針對表示傳回值的 `false` 物件，正確地傳回 <xref:System.Reflection.ParameterInfo> 。 在適用於 Windows 市集應用程式的 .NET 中，它會傳回 `true`。 中繼語言 (IL) 不會直接支援此作業，而是將解譯工作留給語言。

- 不支援 <xref:System.RuntimeFieldHandle> 和 <xref:System.RuntimeMethodHandle> 結構上的公用成員。 只有針對 LINQ、運算式樹狀架構和靜態陣列初始設定，才會支援這些類型。

- <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> 和 <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> 將隱藏的成員包含基底類別中，因此可能會在非明確覆寫的情況下被覆寫。 針對其他 [RuntimeReflectionExtensions.GetRuntime*](xref:System.Reflection.RuntimeReflectionExtensions) 方法也是如此。

- 當您嘗試建立特定的組合 (例如 byref 的陣列) 時，<xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> 和 <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> 不會失敗。

- 您不能使用反映來叫用具有指標參數的成員。

- 您不能使用反映來取得或設定指標欄位。

- 當引數計數錯誤, 且其中一個引數的類型不正確時, .NET Native <xref:System.ArgumentException>會擲回, 而不<xref:System.Reflection.TargetParameterCountException>是。

- 通常不支援例外狀況的二進位序列化。 因此，可以將不可序列化的物件加入 <xref:System.Exception.Data%2A?displayProperty=nameWithType> 字典。

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a>不支援的案例和 API

下列各節會針對一般開發、interop 以及 HTTPClient 和 Windows Communication Foundation (WCF) 等技術，列出不支援的案例和 API：

- [一般開發](#General)

- [HttpClient](#HttpClient)

- [Interop](#Interop)

- [不支援的 API](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a>一般開發的差異

**值類型**

- 如果您覆寫 <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> 和 <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> 方法的值類型，請勿呼叫基底類別實作。 在適用於 Windows 市集應用程式的 .NET 中，這些方法會依賴反映。 在編譯時期, .NET Native 會產生不依賴執行時間反映的執行。 這表示, 如果您未覆寫這兩個方法, 它們會如預期般運作, 因為 .NET Native 會在編譯時期產生實作為。 不過，覆寫這些方法，但又呼叫基底類別實作，將會導致例外狀況。

- 不支援大於 1 MB 的值類型。

- 實值型別在 .NET Native 中不能有無參數的函數。 (C#和 Visual Basic 在實數值型別上禁止無參數的構造函式。 不過，可以在 IL 中建立這些預設建構函式)。

**陣列**

- 不支援下限不是零的陣列。 一般而言，可以呼叫 <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> 多載來建立這些陣列。

- 不支援動態建立多維陣列。 這類陣列的建立，通常是藉由呼叫包含 <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> 參數之 `lengths` 方法的多載，或是呼叫 <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> 方法。

- 不支援具有 4 個 (含) 以上維度的多維陣列，意即，其 <xref:System.Array.Rank%2A?displayProperty=nameWithType> 屬性值為 4 (含) 以上。 請改用 [不規則陣列](../../csharp/programming-guide/arrays/jagged-arrays.md) (陣列的陣列)。 例如， `array[x,y,z]` 無效，但 `array[x][y][z]` 有效。

- 不支援多維陣列的變異數，它會在執行階段導致 <xref:System.InvalidCastException> 例外狀況。

**泛型**

- 無限的泛型類型擴充會導致編譯器錯誤。 例如，此程式碼無法編譯：

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

**Pointers**

- 不支援指標的陣列。

- 您不能使用反映來取得或設定指標欄位。

**序列化**

不支援 <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> 屬性。 請改用 <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> 屬性。

**資源**

不支援將當地語系化的資源與 <xref:System.Diagnostics.Tracing.EventSource> 類別搭配使用。 <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> 屬性不會定義當地語系化的資源。

**委派**

不支援`Delegate.BeginInvoke` 和 `Delegate.EndInvoke` 。

**其他 API**

- <xref:System.PlatformNotSupportedException> 如果<xref:System.Runtime.InteropServices.GuidAttribute>屬性未套用至型別, 則 [TypeInfo GUID](xref:System.Type.GUID)屬性會擲回例外狀況。 GUID 主要用於 COM 支援。

- <xref:System.DateTime.Parse%2A?displayProperty=nameWithType>方法會正確剖析在 .NET Native 中包含簡短日期的字串。 不過，它不會維護 Microsoft 知識庫文章 [KB2803771](https://support.microsoft.com/kb/2803771) 和 [KB2803755](https://support.microsoft.com/kb/2803755)中描述之日期和時間剖析變更的相容性。

- <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")`會在 .NET Native 中正確舍入。 在某些版本的 CLR 中，會將結果字串無條件捨去，而不是四捨五入。

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a>HttpClient 差異

在 .NET Native 中, <xref:System.Net.Http.HttpClientHandler>類別會在內部使用 WinINet ( <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter>透過類別), 而<xref:System.Net.WebRequest>不<xref:System.Net.WebResponse>是在適用于 Windows Store 應用程式的標準 .net 中使用的和類別。  WinINet 並未支援 <xref:System.Net.Http.HttpClientHandler> 類別支援的所有組態選項。  因此：

- 上<xref:System.Net.Http.HttpClientHandler> `true`的一些功能屬性會在 .NET Native 上傳回, 而它們會在適用于 Windows Store 應用程式的標準 .net 中傳回。 `false`

- 某些設定屬性`get`存取子一律會傳回 .NET Native 上的固定值, 這與適用于 Windows Store 應用程式的 .net 中預設的可設定值不同。

下列各小節會說明一些其他的行為差異。

**Proxy**

<xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter>類別不支援根據要求來設定或覆寫 proxy。  這表示 .NET Native 上的所有要求都會使用系統設定的 proxy 伺服器或沒有 proxy 伺服器, 端視<xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType>屬性的值而定。  在適用於 Windows 市集應用程式的 .NET 中，是由 <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> 屬性來定義 Proxy 伺服器。  在 .NET Native 上, 將<xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType>設定為以外的值`null` , 則<xref:System.PlatformNotSupportedException>會擲回例外狀況。  屬性會在 .NET Native 上傳回, 而它會在適用于 Windows Store 應用程式的標準 .NET Framework 中返回`true`。 <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> `false`

**自動重新導向**

<xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter>類別不允許設定自動重新導向的數目上限。  在適用於 Windows 市集應用程式的標準 .NET 中， <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> 屬性的值預設為 50，而且可以修改。 在 .NET Native 上, 這個屬性的值是 10, 而嘗試修改它<xref:System.PlatformNotSupportedException>會擲回例外狀況。  屬性會在 .NET Native 上傳回, 而在適用于WindowsStore應用程式的.net中則會傳回。`true` `false` <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType>

**自動解壓縮**

適用於 Windows 市集應用程式的 .NET 可讓您將 <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> 屬性設為 <xref:System.Net.DecompressionMethods.Deflate>、 <xref:System.Net.DecompressionMethods.GZip>、 <xref:System.Net.DecompressionMethods.Deflate> 和 <xref:System.Net.DecompressionMethods.GZip>同時設定，或是設為 <xref:System.Net.DecompressionMethods.None>。  .NET Native 只支援<xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip>搭配、或<xref:System.Net.DecompressionMethods.None>。  嘗試以無訊息模式將 <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> 屬性單獨設為 <xref:System.Net.DecompressionMethods.Deflate> 或 <xref:System.Net.DecompressionMethods.GZip> ，會將其設為同時使用 <xref:System.Net.DecompressionMethods.Deflate> 和 <xref:System.Net.DecompressionMethods.GZip>。

**Cookie**

<xref:System.Net.Http.HttpClient> 和 WinINet 會同時執行 Cookie 處理作業。  <xref:System.Net.CookieContainer> 所產生的 Cookie 會與 WinINet Cookie 快取中的 Cookie 合併。  從 <xref:System.Net.CookieContainer> 移除 Cookie 會防止 <xref:System.Net.Http.HttpClient> 傳送 Cookie，但如果 WinINet 已經看到 Cookie，而且使用者沒有刪除 Cookie，WinINet 就會加以傳送。  若要使用 <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>或 <xref:System.Net.CookieContainer> API，以程式設計方式將 Cookie 從 WinINet 移除是不可能的。  將 <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> 屬性設為 `false` 只會導致 <xref:System.Net.Http.HttpClient> 停止傳送 Cookie，WinINet 還是會在要求中包含其 Cookie。

**認證**

在適用於 Windows 市集應用程式的 .NET 中， <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> 和 <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> 屬性會獨立運作。  此外， <xref:System.Net.Http.HttpClientHandler.Credentials%2A> 屬性會接受實作 <xref:System.Net.ICredentials> 介面的任何物件。  在 .NET Native 中, 將<xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A>屬性設定`true`為會<xref:System.Net.Http.HttpClientHandler.Credentials%2A>使屬性變成`null`。  此外， <xref:System.Net.Http.HttpClientHandler.Credentials%2A> 屬性只能設為 `null`、 <xref:System.Net.CredentialCache.DefaultCredentials%2A>，或是 <xref:System.Net.NetworkCredential>類型的物件。  將任何其他 <xref:System.Net.ICredentials> 物件 (最常用的是 <xref:System.Net.CredentialCache>) 指派給 <xref:System.Net.Http.HttpClientHandler.Credentials%2A> 屬性會擲回 <xref:System.PlatformNotSupportedException>。

**其他不受支援或不可設定的功能**

在 .NET Native:

- <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> 屬性的值一律為 <xref:System.Net.Http.ClientCertificateOption.Automatic>。  在適用於 Windows 市集應用程式的 .NET 中，預設值為 <xref:System.Net.Http.ClientCertificateOption.Manual>。

- <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> 屬性不可設定。

- <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> 屬性一律為 `true`。  在適用於 Windows 市集應用程式的 .NET 中，預設值為 `false`。

- 系統會將回應中的 `SetCookie2` 標頭視為過時而將它忽略。

<a name="Interop"></a>
### <a name="interop-differences"></a>Interop 的差異
 **已被取代的 API**

 有些與 Managed 程式碼交互操作的不常用 API 已被取代。 與 .NET Native 搭配使用時, 這些 api 可能會<xref:System.NotImplementedException>擲<xref:System.PlatformNotSupportedException>回或例外狀況, 或導致編譯器錯誤。 在適用於 Windows 市集應用程式的 .NET 中，這些 API 會標示為已過時，但是呼叫這些 API 會產生編譯器警告，而不是編譯器錯誤。

 已淘汰的`VARIANT`封送處理 api 包括:

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 可支援<xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> ，但在某些情況下，它會擲回例外狀況，例如用於 [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) 或 byref 變異數時。

 適用于[IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)支援的已淘汰 api 包括:

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

傳統 COM 事件的已淘汰 Api 包括:

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>介面中的已淘汰 api (.NET Native 不支援) 包含:

- <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>(所有成員)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>(所有成員)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>(所有成員)
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

其他不支援的 interop 功能包括:

- <xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>(所有成員)
- <xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>(所有成員)
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 很少使用的封送處理 Api:

- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>

 **平台叫用和 COM interop 相容性**

 .NET Native 中仍然支援大部分的平台叫用和 COM Interop 案例。 特別是仍支援與 Windows 執行階段 (WinRT) API 的所有交互操作性，以及 Windows 執行階段需要的所有封送處理。 其中包括對下列項目的封送處理支援：

- 陣列 (包括 <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)

- `BStr`

- 委派

- 字串 (Unicode、Ansi 和 HSTRING)

- 結構 (`byref` 和 `byval`)

- 等位

- Win32 控制代碼

- 所有 WinRT 結構

- 部分支援封送處理變異數類型。 支援的項目如下：

  - <xref:System.Boolean>

  - <xref:System.Byte>

  - <xref:System.Decimal>

  - <xref:System.Double>

  - <xref:System.Int16>

  - <xref:System.Int32>

  - <xref:System.Int64>

  - <xref:System.SByte>

  - <xref:System.Single>

  - <xref:System.UInt16>

  - <xref:System.UInt32>

  - <xref:System.UInt64>

  - `BStr`

  - [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

不過, .NET Native 不支援下列各項:

- 使用傳統 COM 事件

- 在 Managed 類型上實作 <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> 介面

- 透過 [屬性，在 Managed 類型上實作](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) IDispatch <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> 介面。 不過，請注意您不能透過 `IDispatch`來呼叫 COM 物件，而且您的 Managed 物件不能實作 `IDispatch`。

不支援使用反映來叫用平台叫用方法。 若要解除決這項限制，您可以將此方法呼叫包裝在另一個方法中，並改用反映來呼叫包裝函式。

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>其他與適用於 Windows 市集應用程式的 .NET API 的差異

本節列出 .NET Native 中不支援的其餘 Api。 不受支援的的最大 API 集是 Windows Communication Foundation (WCF) API。

**DataAnnotations (System.ComponentModel.DataAnnotations)**

.NET Native 中不支援<xref:System.ComponentModel.DataAnnotations>和<xref:System.ComponentModel.DataAnnotations.Schema>命名空間中的類型。 其中包括下列在適用于 Windows 8 的 Windows Store 應用程式的 .NET 中出現的類型:

- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>

 **Visual Basic**

.NET Native 目前不支援 Visual Basic。 在 .NET Native 中<xref:Microsoft.VisualBasic> , 無法使用<xref:Microsoft.VisualBasic.CompilerServices>和命名空間中的下列類型:

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>

**反映內容 (System.Reflection.Context 命名空間)**

.NET Native 中不支援類別。<xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType>

**RTC (System.Net.Http.Rtc)**

.NET Native 中不支援類別。`System.Net.Http.RtcRequestFactory`

**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**

.NET Native 中不支援[system.servicemodel. * 命名空間](xref:System.ServiceModel)中的類型。 其中包括下列類型：

- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>

### <a name="differences-in-serializers"></a>序列化程式的差異

下列差異與使用 <xref:System.Runtime.Serialization.DataContractSerializer>、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>和 <xref:System.Xml.Serialization.XmlSerializer> 類別來進行序列化和還原序列化有關。

- 在 .NET Native 中<xref:System.Runtime.Serialization.DataContractSerializer> , <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>和無法序列化或還原序列化具有基類成員 (其類型不是根序列化類型) 的衍生類別。 例如，在下列程式碼中，嘗試序列化或還原序列化 `Y` 會產生錯誤：

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  序列化程式無法識別 `InnerType` 類型，因為在序列化期間，並未周遊基底類別的成員。

- <xref:System.Runtime.Serialization.DataContractSerializer> 和 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 無法將實作 <xref:System.Collections.Generic.IEnumerable%601> 介面的類別或結構序列化。 例如，下列的類型無法序列化或還原序列化：

- <xref:System.Xml.Serialization.XmlSerializer> 無法將下列物件值序列化，因為它不知道要序列化之物件的確切類型：

- 如果已序列化物件的類型是<xref:System.Xml.Serialization.XmlSerializer> ，則 <xref:System.Xml.XmlQualifiedName>無法序列化或還原序列化。

- 所有序列化程式 (<xref:System.Runtime.Serialization.DataContractSerializer>、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>和 <xref:System.Xml.Serialization.XmlSerializer>) 都無法為 <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> 類型或是包含 <xref:System.Xml.Linq.XElement>的類型產生序列化程式碼， 而會顯示建置時間錯誤。

- 無法保證序列化類型的下列建構函式能夠如預期般運作：

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=nameWithType>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=nameWithType>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=nameWithType>

- 如果類型中有使用下列任何屬性的方法，則<xref:System.Xml.Serialization.XmlSerializer> 無法為該類型產生程式碼：

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <xref:System.Xml.Serialization.XmlSerializer> 不接受 <xref:System.Xml.Serialization.IXmlSerializable> 自訂序列化介面。 如果您有實作這個介面的類別， <xref:System.Xml.Serialization.XmlSerializer> 會將該類型視為簡單的 CLR 物件 (POCO) 類型，並且只將其公開屬性序列化。

- 序列化一般<xref:System.Exception>物件無法與<xref:System.Runtime.Serialization.DataContractSerializer>和<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>搭配運作。

<a name="VS"></a>

## <a name="visual-studio-differences"></a>Visual Studio 的差異

**例外狀況和偵錯**

當您使用偵錯工具中的 .NET Native 來執行以編譯的應用程式時, 會針對下列例外狀況類型啟用第一個可能發生的例外狀況:

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

**建置應用程式**

使用 Visual Studio 預設使用的 x86 建置工具。 我們不建議使用 AMD64 MSBuild 工具 (可以在 C:\Program Files (x86)\MSBuild\12.0\bin\amd64 中找到)；這些工具可能會造成組建問題。

**分析工具**

- Visual Studio CPU 分析工具和 XAML 記憶體分析工具不會正確顯示 Just-My-Code。

- XAML 記憶體分析工具不會準確地顯示 Managed 堆積資料。

- CPU 分析工具不會正確地識別模組，並且會顯示具有前置詞的函式名稱。

**單元測試程式庫專案**

不支援在 Windows Store 應用程式專案的單元測試程式庫上啟用 .NET Native, 而且會導致專案無法建立。

## <a name="see-also"></a>另請參閱

- [快速入門](getting-started-with-net-native.md)
- [執行階段指示詞 (rd.xml) 組態檔參考](runtime-directives-rd-xml-configuration-file-reference.md)
- [適用于 Windows Store 應用程式的 .NET 總覽](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [Windows 市集應用程式和 Windows 執行階段的 .NET Framework 支援](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
