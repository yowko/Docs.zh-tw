---
title: 原型消息 - gRPC，面向 WCF 開發人員
description: 瞭解如何在 IDL 中定義 Protobuf 消息並在 C# 中生成。
ms.date: 09/09/2019
ms.openlocfilehash: 5b3d4383de39a3785ef804fec21939a740f54669
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79147980"
---
# <a name="protobuf-messages"></a><span data-ttu-id="c4004-103">Protobuf 訊息</span><span class="sxs-lookup"><span data-stu-id="c4004-103">Protobuf messages</span></span>

<span data-ttu-id="c4004-104">本節介紹如何在`.proto`檔中聲明協定緩衝區（Protobuf）消息。</span><span class="sxs-lookup"><span data-stu-id="c4004-104">This section covers how to declare Protocol Buffer (Protobuf) messages in `.proto` files.</span></span> <span data-ttu-id="c4004-105">它解釋了欄位數和類型的基本概念，並查看`protoc`編譯器生成的 C# 代碼。</span><span class="sxs-lookup"><span data-stu-id="c4004-105">It explains the fundamental concepts of field numbers and types, and it looks at the C# code that the `protoc` compiler generates.</span></span>

<span data-ttu-id="c4004-106">本章的其餘部分將更詳細地介紹在 Protobuf 中如何表示不同類型的資料。</span><span class="sxs-lookup"><span data-stu-id="c4004-106">The rest of the chapter will look in more detail at how different types of data are represented in Protobuf.</span></span>

## <a name="declaring-a-message"></a><span data-ttu-id="c4004-107">聲明消息</span><span class="sxs-lookup"><span data-stu-id="c4004-107">Declaring a message</span></span>

<span data-ttu-id="c4004-108">在 Windows 通信基礎 （WCF） 中，股票市場交易應用程式的`Stock`類可以定義如下示例：</span><span class="sxs-lookup"><span data-stu-id="c4004-108">In Windows Communication Foundation (WCF), a `Stock` class for a stock market trading application might be defined like the following example:</span></span>

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

<span data-ttu-id="c4004-109">要在 Protobuf 中實現等效類，必須在`.proto`檔中聲明它。</span><span class="sxs-lookup"><span data-stu-id="c4004-109">To implement the equivalent class in Protobuf, you must declare it in the `.proto` file.</span></span> <span data-ttu-id="c4004-110">然後`protoc`，編譯器將生成 .NET 類作為生成過程的一部分。</span><span class="sxs-lookup"><span data-stu-id="c4004-110">The `protoc` compiler will then generate the .NET class as part of the build process.</span></span>

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

<span data-ttu-id="c4004-111">第一行聲明正在使用的語法版本。</span><span class="sxs-lookup"><span data-stu-id="c4004-111">The first line declares the syntax version being used.</span></span> <span data-ttu-id="c4004-112">該語言版本 3 于 2016 年發佈。</span><span class="sxs-lookup"><span data-stu-id="c4004-112">Version 3 of the language was released in 2016.</span></span> <span data-ttu-id="c4004-113">它是我們為 gRPC 服務推薦的版本。</span><span class="sxs-lookup"><span data-stu-id="c4004-113">It's the version that we recommend for gRPC services.</span></span>

<span data-ttu-id="c4004-114">該`option csharp_namespace`行指定要用於生成的 C# 類型的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c4004-114">The `option csharp_namespace` line specifies the namespace to be used for the generated C# types.</span></span> <span data-ttu-id="c4004-115">在為其他語言編譯檔時，`.proto`將忽略此選項。</span><span class="sxs-lookup"><span data-stu-id="c4004-115">This option will be ignored when the `.proto` file is compiled for other languages.</span></span> <span data-ttu-id="c4004-116">Protobuf 檔通常包含多種語言的語言特定選項。</span><span class="sxs-lookup"><span data-stu-id="c4004-116">Protobuf files often contain language-specific options for several languages.</span></span>

<span data-ttu-id="c4004-117">消息`Stock`定義指定四個欄位。</span><span class="sxs-lookup"><span data-stu-id="c4004-117">The `Stock` message definition specifies four fields.</span></span> <span data-ttu-id="c4004-118">每個都有一個類型、一個名稱和一個欄位編號。</span><span class="sxs-lookup"><span data-stu-id="c4004-118">Each has a type, a name, and a field number.</span></span>

## <a name="field-numbers"></a><span data-ttu-id="c4004-119">欄位編號</span><span class="sxs-lookup"><span data-stu-id="c4004-119">Field numbers</span></span>

<span data-ttu-id="c4004-120">欄位編號是 Protobuf 的重要組成部分。</span><span class="sxs-lookup"><span data-stu-id="c4004-120">Field numbers are an important part of Protobuf.</span></span> <span data-ttu-id="c4004-121">它們用於標識二進位編碼資料中的欄位，這意味著它們無法從服務的版本更改為版本。</span><span class="sxs-lookup"><span data-stu-id="c4004-121">They're used to identify fields in the binary encoded data, which means they can't change from version to version of your service.</span></span> <span data-ttu-id="c4004-122">優點是向後相容性和正向相容性是可能的。</span><span class="sxs-lookup"><span data-stu-id="c4004-122">The advantage is that backward compatibility and forward compatibility are possible.</span></span> <span data-ttu-id="c4004-123">只要處理丟失值的可能性，用戶端和服務將忽略他們不知道的欄位編號。</span><span class="sxs-lookup"><span data-stu-id="c4004-123">Clients and services will simply ignore field numbers that they don't know about, as long as the possibility of missing values is handled.</span></span>

<span data-ttu-id="c4004-124">在二進位格式中，欄位編號與類型識別碼組合。</span><span class="sxs-lookup"><span data-stu-id="c4004-124">In the binary format, the field number is combined with a type identifier.</span></span> <span data-ttu-id="c4004-125">欄位編號從 1 到 15 可以編碼其類型為單個位元組。</span><span class="sxs-lookup"><span data-stu-id="c4004-125">Field numbers from 1 to 15 can be encoded with their type as a single byte.</span></span> <span data-ttu-id="c4004-126">從 16 到 2，047 的數位需要 2 個位元組。</span><span class="sxs-lookup"><span data-stu-id="c4004-126">Numbers from 16 to 2,047 take 2 bytes.</span></span> <span data-ttu-id="c4004-127">如果出於任何原因需要郵件上的 2，047 個欄位，則可以走高。</span><span class="sxs-lookup"><span data-stu-id="c4004-127">You can go higher if you need more than 2,047 fields on a message for any reason.</span></span> <span data-ttu-id="c4004-128">欄位號 1 到 15 的單個位元組識別碼提供了更好的性能，因此應將它們用於最基本、最常用的欄位。</span><span class="sxs-lookup"><span data-stu-id="c4004-128">The single byte identifiers for field numbers 1 to 15 offer better performance, so you should use them for the most basic, frequently used fields.</span></span>

## <a name="types"></a><span data-ttu-id="c4004-129">類型</span><span class="sxs-lookup"><span data-stu-id="c4004-129">Types</span></span>

<span data-ttu-id="c4004-130">型別宣告使用 Protobuf 的本機純量資料型別，[下一節](protobuf-data-types.md)將更詳細地討論這些類型。</span><span class="sxs-lookup"><span data-stu-id="c4004-130">The type declarations are using Protobuf's native scalar data types, which are discussed in more detail in [the next section](protobuf-data-types.md).</span></span> <span data-ttu-id="c4004-131">本章的其餘部分將介紹 Protobuf 的內置類型，並展示它們與常見的 .NET 類型的關係。</span><span class="sxs-lookup"><span data-stu-id="c4004-131">The rest of this chapter will cover Protobuf's built-in types and show how they relate to common .NET types.</span></span>

> [!NOTE]
> <span data-ttu-id="c4004-132">Protobuf 不支援本機`decimal`類型，因此`double`使用。</span><span class="sxs-lookup"><span data-stu-id="c4004-132">Protobuf doesn't natively support a `decimal` type, so `double` is used instead.</span></span> <span data-ttu-id="c4004-133">對於需要全小數精度的應用程式，請參閱本章下一部分[中有關小數部分](protobuf-data-types.md#decimals)的部分。</span><span class="sxs-lookup"><span data-stu-id="c4004-133">For applications that require full decimal precision, refer to the [section on decimals](protobuf-data-types.md#decimals) in the next part of this chapter.</span></span>

## <a name="the-generated-code"></a><span data-ttu-id="c4004-134">產生的程式碼</span><span class="sxs-lookup"><span data-stu-id="c4004-134">The generated code</span></span>

<span data-ttu-id="c4004-135">生成應用程式時，Protobuf 會為每個消息創建類，將其本機類型映射到 C# 類型。</span><span class="sxs-lookup"><span data-stu-id="c4004-135">When you build your application, Protobuf creates classes for each of your messages, mapping its native types to C# types.</span></span> <span data-ttu-id="c4004-136">生成的`Stock`類型將具有以下簽名：</span><span class="sxs-lookup"><span data-stu-id="c4004-136">The generated `Stock` type would have the following signature:</span></span>

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

<span data-ttu-id="c4004-137">生成的實際代碼要比這更複雜得多。</span><span class="sxs-lookup"><span data-stu-id="c4004-137">The actual code that's generated is far more complicated than this.</span></span> <span data-ttu-id="c4004-138">原因是每個類都包含序列化自身並將其反序列化為二進位線格式所需的所有代碼。</span><span class="sxs-lookup"><span data-stu-id="c4004-138">The reason is that each class contains all the code necessary to serialize and deserialize itself to the binary wire format.</span></span>

### <a name="property-names"></a><span data-ttu-id="c4004-139">屬性名稱</span><span class="sxs-lookup"><span data-stu-id="c4004-139">Property names</span></span>

<span data-ttu-id="c4004-140">請注意，Protobuf 編譯器應用於`PascalCase`屬性名稱，儘管它們位於`snake_case``.proto`檔中。</span><span class="sxs-lookup"><span data-stu-id="c4004-140">Note that the Protobuf compiler applied `PascalCase` to the property names, although they were `snake_case` in the `.proto` file.</span></span> <span data-ttu-id="c4004-141">[Protobuf 樣式指南](https://developers.google.com/protocol-buffers/docs/style)建議`snake_case`在消息定義中使用，以便其他平臺的代碼生成生成其約定的預期情況。</span><span class="sxs-lookup"><span data-stu-id="c4004-141">The [Protobuf style guide](https://developers.google.com/protocol-buffers/docs/style) recommends using `snake_case` in your message definitions so that the code generation for other platforms produces the expected case for their conventions.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c4004-142">[上一個](protocol-buffers.md)
>[下一個](protobuf-data-types.md)</span><span class="sxs-lookup"><span data-stu-id="c4004-142">[Previous](protocol-buffers.md)
[Next](protobuf-data-types.md)</span></span>
