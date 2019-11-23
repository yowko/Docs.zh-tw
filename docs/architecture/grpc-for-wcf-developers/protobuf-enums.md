---
title: Protobuf 列舉-適用于 WCF 開發人員的 gRPC
description: 瞭解如何在 Protobuf 中宣告和使用列舉。
ms.date: 09/09/2019
ms.openlocfilehash: 4ea4d03bede2a9ebfd1f2c3ee56f299e918800e9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971582"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="b8bbb-103">Protobuf 列舉</span><span class="sxs-lookup"><span data-stu-id="b8bbb-103">Protobuf enumerations</span></span>

<span data-ttu-id="b8bbb-104">Protobuf 支援列舉類型，如上一節中所示，列舉是用來判斷 `oneof` 欄位的類型。</span><span class="sxs-lookup"><span data-stu-id="b8bbb-104">Protobuf supports enumeration types, as seen in the previous section where an enum was used to determine the type of a `oneof` field.</span></span> <span data-ttu-id="b8bbb-105">您可以定義自己的列舉類型，而 Protobuf 會將它們C#編譯成列舉類型。</span><span class="sxs-lookup"><span data-stu-id="b8bbb-105">You can define your own enumeration types and Protobuf will compile them to C# enum types.</span></span> <span data-ttu-id="b8bbb-106">由於 Protobuf 可以與不同的C#語言搭配使用，因此列舉的命名慣例與慣例不同。</span><span class="sxs-lookup"><span data-stu-id="b8bbb-106">Since Protobuf can be used with different languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="b8bbb-107">不過，程式碼產生器非常聰明，而且會將名稱轉換C#成傳統案例。</span><span class="sxs-lookup"><span data-stu-id="b8bbb-107">However, the code generator is clever and converts the names to the traditional C# case.</span></span> <span data-ttu-id="b8bbb-108">如果與此功能變數名稱相等的 Pascal 大小寫是以列舉名稱開頭，則會將它移除。</span><span class="sxs-lookup"><span data-stu-id="b8bbb-108">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="b8bbb-109">例如，在此 Protobuf 列舉中，欄位前面會加上 `ACCOUNT_STATUS`，這相當於 Pascal 案例列舉名稱： `AccountStatus`。</span><span class="sxs-lookup"><span data-stu-id="b8bbb-109">For example, in this Protobuf enumeration the fields are prefixed with `ACCOUNT_STATUS`, which is equivalent to the Pascal case enum name: `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="b8bbb-110">因此，產生器會建立C#相當於下列程式碼的列舉：</span><span class="sxs-lookup"><span data-stu-id="b8bbb-110">So, the generator creates a C# enum equivalent to the following code:</span></span>

```csharp
public enum AccountStatus
{
    Unknown = 0,
    Pending = 1,
    Active = 2,
    Suspended = 3,
    Closed = 4
}
```

<span data-ttu-id="b8bbb-111">Protobuf 列舉定義**必須**有零常數做為其第一個欄位。</span><span class="sxs-lookup"><span data-stu-id="b8bbb-111">Protobuf enumeration definitions **must** have a zero constant as their first field.</span></span> <span data-ttu-id="b8bbb-112">如同在C#中，您可以宣告多個具有相同值的欄位，但您必須使用列舉中的 `allow_alias` 選項明確啟用此選項：</span><span class="sxs-lookup"><span data-stu-id="b8bbb-112">As in C#, you can declare multiple fields with the same value, but you must explicitly enable this option using the `allow_alias` option in the enum:</span></span>

```protobuf
enum AccountStatus {
  option allow_alias = true;
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
  ACCOUNT_STATUS_CANCELLED = 4;
}
```

<span data-ttu-id="b8bbb-113">您可以在 `.proto` 檔案的最上層宣告列舉，或在訊息定義內進行宣告。</span><span class="sxs-lookup"><span data-stu-id="b8bbb-113">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="b8bbb-114">嵌套的列舉型別（例如，嵌套訊息）將會在產生之 message 類別的 `.Types` 靜態類別中宣告。</span><span class="sxs-lookup"><span data-stu-id="b8bbb-114">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="b8bbb-115">沒有任何方法可將[[Flags]](xref:System.FlagsAttribute)屬性套用至 Protobuf 產生的列舉，Protobuf 也不了解位列舉組合。</span><span class="sxs-lookup"><span data-stu-id="b8bbb-115">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="b8bbb-116">請看下列範例：</span><span class="sxs-lookup"><span data-stu-id="b8bbb-116">Take a look at the following example:</span></span>

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region available_in = 1;
}
```

<span data-ttu-id="b8bbb-117">如果您將 `product.AvailableIn` 設定為 `Region.NorthAmerica | Region.SouthAmerica`，則會將它序列化為整數值 `3`。</span><span class="sxs-lookup"><span data-stu-id="b8bbb-117">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="b8bbb-118">當用戶端或伺服器嘗試將值還原序列化時，它在 `3` 的 enum 定義中找不到相符項，因此會 `Region.None`結果。</span><span class="sxs-lookup"><span data-stu-id="b8bbb-118">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3` and the result will be `Region.None`.</span></span>

<span data-ttu-id="b8bbb-119">在 Protobuf 中處理多個列舉值的最佳方式是使用列舉類型的 `repeated` 欄位。</span><span class="sxs-lookup"><span data-stu-id="b8bbb-119">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b8bbb-120">[上一頁](protobuf-any-oneof.md)
>[下一頁](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="b8bbb-120">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
