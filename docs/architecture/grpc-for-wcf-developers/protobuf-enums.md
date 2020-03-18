---
title: 原數枚 - gRPC 面向 WCF 開發人員
description: 瞭解如何在 Protobuf 中聲明和使用枚舉。
ms.date: 09/09/2019
ms.openlocfilehash: 2177f568a671fa0e651625c6e025ac70c243feb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148071"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="91e22-103">Protobuf 列舉</span><span class="sxs-lookup"><span data-stu-id="91e22-103">Protobuf enumerations</span></span>

<span data-ttu-id="91e22-104">Protobuf 支援枚舉類型。</span><span class="sxs-lookup"><span data-stu-id="91e22-104">Protobuf supports enumeration types.</span></span> <span data-ttu-id="91e22-105">您在上一節中看到了此支援，其中使用枚舉來確定`Oneof`欄位的類型。</span><span class="sxs-lookup"><span data-stu-id="91e22-105">You saw this support in the previous section, where an enum was used to determine the type of a `Oneof` field.</span></span> <span data-ttu-id="91e22-106">您可以定義自己的枚舉類型，Protobuf 將將它們編譯為 C# 枚舉類型。</span><span class="sxs-lookup"><span data-stu-id="91e22-106">You can define your own enumeration types, and Protobuf will compile them to C# enum types.</span></span>

<span data-ttu-id="91e22-107">由於您可以將 Protobuf 用於各種語言，因此枚舉的命名約定與 C# 約定不同。</span><span class="sxs-lookup"><span data-stu-id="91e22-107">Because you can use Protobuf with various languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="91e22-108">但是，代碼產生器將名稱轉換為傳統的 C# 大小寫。</span><span class="sxs-lookup"><span data-stu-id="91e22-108">However, the code generator converts the names to the traditional C# case.</span></span> <span data-ttu-id="91e22-109">如果欄位名稱的 Pascal 大小寫以枚舉名稱開頭，則將其刪除。</span><span class="sxs-lookup"><span data-stu-id="91e22-109">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="91e22-110">例如，在下面的 Protobuf 枚舉中，欄位用 預綴為`ACCOUNT_STATUS`。</span><span class="sxs-lookup"><span data-stu-id="91e22-110">For example, in the following Protobuf enumeration, the fields are prefixed with `ACCOUNT_STATUS`.</span></span> <span data-ttu-id="91e22-111">此首碼等效于 Pascal 大小寫枚舉名稱`AccountStatus`。</span><span class="sxs-lookup"><span data-stu-id="91e22-111">This prefix is equivalent to the Pascal-case enum name, `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="91e22-112">產生器創建等效于以下代碼的 C# 枚舉：</span><span class="sxs-lookup"><span data-stu-id="91e22-112">The generator creates a C# enum equivalent to the following code:</span></span>

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

<span data-ttu-id="91e22-113">Protobuf 枚舉定義*必須*具有零常量作為第一個欄位。</span><span class="sxs-lookup"><span data-stu-id="91e22-113">Protobuf enumeration definitions *must* have a zero constant as their first field.</span></span> <span data-ttu-id="91e22-114">與 C# 中一樣，您可以聲明具有相同值的多個欄位。</span><span class="sxs-lookup"><span data-stu-id="91e22-114">As in C#, you can declare multiple fields with the same value.</span></span> <span data-ttu-id="91e22-115">但是，您必須使用枚舉中`allow_alias`的選項顯式啟用此選項：</span><span class="sxs-lookup"><span data-stu-id="91e22-115">But you must explicitly enable this option by using the `allow_alias` option in the enum:</span></span>

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

<span data-ttu-id="91e22-116">您可以在`.proto`檔中的頂層聲明枚舉，也可以嵌套在消息定義中。</span><span class="sxs-lookup"><span data-stu-id="91e22-116">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="91e22-117">嵌套枚舉（類似于嵌套消息）將在生成的消息類中的`.Types`靜態類中聲明。</span><span class="sxs-lookup"><span data-stu-id="91e22-117">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="91e22-118">無法將[[Flags]](xref:System.FlagsAttribute)屬性應用於 Protobuf 生成的枚舉，並且 Protobuf 不理解位級枚舉組合。</span><span class="sxs-lookup"><span data-stu-id="91e22-118">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="91e22-119">查看以下示例：</span><span class="sxs-lookup"><span data-stu-id="91e22-119">Look at the following example:</span></span>

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

<span data-ttu-id="91e22-120">如果設置為`product.AvailableIn``Region.NorthAmerica | Region.SouthAmerica`，則序列化為整數值`3`。</span><span class="sxs-lookup"><span data-stu-id="91e22-120">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="91e22-121">當用戶端或伺服器嘗試取消序列化該值時，它不會在 的`3`枚舉定義中找到匹配項。</span><span class="sxs-lookup"><span data-stu-id="91e22-121">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3`.</span></span> <span data-ttu-id="91e22-122">結果將為`Region.None`。</span><span class="sxs-lookup"><span data-stu-id="91e22-122">The result will be `Region.None`.</span></span>

<span data-ttu-id="91e22-123">在 Protobuf 中使用多個枚舉值的最佳方法是使用枚舉類型的`repeated`欄位。</span><span class="sxs-lookup"><span data-stu-id="91e22-123">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="91e22-124">[上一個](protobuf-any-oneof.md)
>[下一個](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="91e22-124">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
