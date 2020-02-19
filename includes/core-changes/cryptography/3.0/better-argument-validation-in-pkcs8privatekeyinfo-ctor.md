---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449206"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="a17ed-101">Pkcs8PrivateKeyInfo 的函式中有更好的引數驗證</span><span class="sxs-lookup"><span data-stu-id="a17ed-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="a17ed-102">從 .NET Core 3.0 Preview 9 開始，`Pkcs8PrivateKeyInfo` 的函式會將 `algorithmParameters` 參數驗證為單一 BER 編碼的值。</span><span class="sxs-lookup"><span data-stu-id="a17ed-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="a17ed-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="a17ed-103">Change description</span></span>

<span data-ttu-id="a17ed-104">在 .NET Core 3.0 Preview 9 之前， [`Pkcs8PrivateKeyInfo`](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))的函式不會驗證 `algorithmParameters` 引數。</span><span class="sxs-lookup"><span data-stu-id="a17ed-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="a17ed-105">當這個引數表示不正確值時，此函式將會成功，但呼叫任何 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>、<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>、<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>或 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> 方法都會擲回不接受的引數 <xref:System.ArgumentException> （`preEncodedValue`）或 <xref:System.Security.Cryptography.CryptographicException>。</span><span class="sxs-lookup"><span data-stu-id="a17ed-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="a17ed-106">如果在 Preview 9 之前以 .NET Core 3.0 執行，下列程式碼只會在呼叫 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> 方法時擲回例外狀況：</span><span class="sxs-lookup"><span data-stu-id="a17ed-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="a17ed-107">從 .NET Core 3.0 Preview 9 開始，引數會在函式中進行驗證，而不正確值會導致方法擲回 <xref:System.Security.Cryptography.CryptographicException>。</span><span class="sxs-lookup"><span data-stu-id="a17ed-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="a17ed-108">這項變更會將例外狀況移到接近資料錯誤的來源。</span><span class="sxs-lookup"><span data-stu-id="a17ed-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="a17ed-109">例如：</span><span class="sxs-lookup"><span data-stu-id="a17ed-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="a17ed-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="a17ed-110">Version introduced</span></span>

<span data-ttu-id="a17ed-111">3.0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="a17ed-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a17ed-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="a17ed-112">Recommended action</span></span>

<span data-ttu-id="a17ed-113">請確定只提供有效的 `algorithmParameters` 值，或如果需要例外狀況處理，則呼叫 `Pkcs8PrivateKeyInfo` 的 <xref:System.ArgumentException> 和 <xref:System.Security.Cryptography.CryptographicException> 測試。</span><span class="sxs-lookup"><span data-stu-id="a17ed-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="a17ed-114">類別</span><span class="sxs-lookup"><span data-stu-id="a17ed-114">Category</span></span>

<span data-ttu-id="a17ed-115">Cryptography</span><span class="sxs-lookup"><span data-stu-id="a17ed-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="a17ed-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a17ed-116">Affected APIs</span></span>

- <span data-ttu-id="a17ed-117">[Pkcs8PrivateKeyInfo 的構造函式](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="a17ed-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
