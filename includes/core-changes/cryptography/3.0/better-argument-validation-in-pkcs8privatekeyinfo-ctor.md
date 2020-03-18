---
ms.openlocfilehash: 8d3a8712528d2d35c706cc26b8c388b65d6ad506
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449206"
---
### <a name="better-argument-validation-in-the-pkcs8privatekeyinfo-constructor"></a><span data-ttu-id="ae13c-101">在 Pkcs8PrivateKeyInfo 建構函式中更好的參數驗證</span><span class="sxs-lookup"><span data-stu-id="ae13c-101">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>

<span data-ttu-id="ae13c-102">從 .NET Core 3.0 預覽`Pkcs8PrivateKeyInfo`9 開始，`algorithmParameters`建構函式將參數驗證為單個 BER 編碼值。</span><span class="sxs-lookup"><span data-stu-id="ae13c-102">Starting with .NET Core 3.0 Preview 9, the `Pkcs8PrivateKeyInfo` constructor validates the `algorithmParameters` parameter as a single BER-encoded value.</span></span>

#### <a name="change-description"></a><span data-ttu-id="ae13c-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="ae13c-103">Change description</span></span>

<span data-ttu-id="ae13c-104">在 .NET Core 3.0 預覽 9 之前，`algorithmParameters`[`Pkcs8PrivateKeyInfo`建構函式](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))未驗證參數。</span><span class="sxs-lookup"><span data-stu-id="ae13c-104">Before .NET Core 3.0 Preview 9, the [`Pkcs8PrivateKeyInfo` constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean)) did not validate the `algorithmParameters` argument.</span></span>  <span data-ttu-id="ae13c-105">當此參數表示無效值時，建構函式將成功，但對任何<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>、 <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>、 或<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A><xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A>方法的調用將引發他們不接受的參數<xref:System.ArgumentException>的 調用 （`preEncodedValue`） 或 。 <xref:System.Security.Cryptography.CryptographicException></span><span class="sxs-lookup"><span data-stu-id="ae13c-105">When this argument represented an invalid value, the constructor would succeed, but a call to any of the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncode%2A>, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encrypt%2A>, or <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.TryEncrypt%2A> methods would throw either an <xref:System.ArgumentException> for an argument they did not accept (`preEncodedValue`) or a <xref:System.Security.Cryptography.CryptographicException>.</span></span>

<span data-ttu-id="ae13c-106">如果在預覽 9 之前使用 .NET Core 3.0 運行，則以下代碼<xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode>僅在調用方法時引發異常：</span><span class="sxs-lookup"><span data-stu-id="ae13c-106">If run with .NET Core 3.0 before Preview 9, the following code throws an exception only when the <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.Encode> method is called:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
// This line throws an ArgumentException for `preEncodedValue`:
byte[] encoded = info.Encode();
```

<span data-ttu-id="ae13c-107">從 .NET Core 3.0 預覽 9 開始，在建構函式中驗證參數，無效值會導致方法引發<xref:System.Security.Cryptography.CryptographicException>。</span><span class="sxs-lookup"><span data-stu-id="ae13c-107">Starting with .NET Core 3.0 Preview 9, the argument is validated in the constructor, and an invalid value results in the method throwing a <xref:System.Security.Cryptography.CryptographicException>.</span></span> <span data-ttu-id="ae13c-108">此更改會使異常更接近資料錯誤的來源。</span><span class="sxs-lookup"><span data-stu-id="ae13c-108">This change moves the exception closer to the source of the data error.</span></span> <span data-ttu-id="ae13c-109">例如：</span><span class="sxs-lookup"><span data-stu-id="ae13c-109">For example:</span></span>

```csharp
byte[] algorithmParameters = { 0x05, 0x00, 0x05, 0x00 };

// This line throws a CryptographicException
var info = new Pkcs8PrivateKeyInfo(algorithmId, algorithmParameters, privateKey);
```

#### <a name="version-introduced"></a><span data-ttu-id="ae13c-110">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="ae13c-110">Version introduced</span></span>

<span data-ttu-id="ae13c-111">3.0 預覽 9</span><span class="sxs-lookup"><span data-stu-id="ae13c-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ae13c-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ae13c-112">Recommended action</span></span>

<span data-ttu-id="ae13c-113">確保僅提供有效的`algorithmParameters`值，或者對`Pkcs8PrivateKeyInfo`建構函式測試的調用以及<xref:System.ArgumentException><xref:System.Security.Cryptography.CryptographicException>如果需要異常處理。</span><span class="sxs-lookup"><span data-stu-id="ae13c-113">Ensure that only valid `algorithmParameters` values are provided, or that calls to the `Pkcs8PrivateKeyInfo` constructor test for both <xref:System.ArgumentException> and <xref:System.Security.Cryptography.CryptographicException> if exception handling is desired.</span></span>

### <a name="category"></a><span data-ttu-id="ae13c-114">類別</span><span class="sxs-lookup"><span data-stu-id="ae13c-114">Category</span></span>

<span data-ttu-id="ae13c-115">Cryptography</span><span class="sxs-lookup"><span data-stu-id="ae13c-115">Cryptography</span></span>

### <a name="affected-apis"></a><span data-ttu-id="ae13c-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ae13c-116">Affected APIs</span></span>

- <span data-ttu-id="ae13c-117">[Pkcs8私人資訊建構函式](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span><span class="sxs-lookup"><span data-stu-id="ae13c-117">[Pkcs8PrivateKeyInfo constructor](xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.%23ctor(System.Security.Cryptography.Oid,System.Nullable%7BSystem.ReadOnlyMemory%7BSystem.Byte%7D%7D,System.ReadOnlyMemory%7BSystem.Byte%7D,System.Boolean))</span></span>

<!--

### Affected APIs

- `M:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo.#ctor(System.Security.Cryptography.Oid,System.Nullable{System.ReadOnlyMemory{System.Byte}},System.ReadOnlyMemory{System.Byte},System.Boolean)`

-->
