---
title: 作法：使用自動實作的屬性來實作輕量型類別 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 626a44fbaa65f48e0d9fe66d83c44abb07eba379
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926764"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="0692b-102">作法：使用自動實作的屬性來實作輕量型類別 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="0692b-102">How to: Implement a Lightweight Class with Auto-Implemented Properties (C# Programming Guide)</span></span>

<span data-ttu-id="0692b-103">這個範例顯示如何建立不可變的輕量型類別，只用來封裝一組自動實作屬性。</span><span class="sxs-lookup"><span data-stu-id="0692b-103">This example shows how to create an immutable lightweight class that serves only to encapsulate a set of auto-implemented properties.</span></span> <span data-ttu-id="0692b-104">當您必須使用參考類型語意時，請使用這種建構，而不是結構。</span><span class="sxs-lookup"><span data-stu-id="0692b-104">Use this kind of construct instead of a struct when you must use reference type semantics.</span></span>

<span data-ttu-id="0692b-105">您可以使用兩種方式建立固定屬性：</span><span class="sxs-lookup"><span data-stu-id="0692b-105">You can make an immutable property in two ways:</span></span>

- <span data-ttu-id="0692b-106">您可以將 [set](../../language-reference/keywords/set.md) 存取子宣告為 [private](../../language-reference/keywords/private.md)。</span><span class="sxs-lookup"><span data-stu-id="0692b-106">You can declare the [set](../../language-reference/keywords/set.md) accessor to be [private](../../language-reference/keywords/private.md).</span></span>  <span data-ttu-id="0692b-107">屬性只有在類型內才可設定，但是它對於使用者而言是不可變的。</span><span class="sxs-lookup"><span data-stu-id="0692b-107">The property is only settable within the type, but it is immutable to consumers.</span></span>

  <span data-ttu-id="0692b-108">當您宣告私用 `set` 存取子時，則無法使用物件初始設定式來初始化屬性。</span><span class="sxs-lookup"><span data-stu-id="0692b-108">When you declare a private `set` accessor, you cannot use an object initializer to initialize the property.</span></span> <span data-ttu-id="0692b-109">您必須使用建構函式或 Factory 方法。</span><span class="sxs-lookup"><span data-stu-id="0692b-109">You must use a constructor or a factory method.</span></span>
- <span data-ttu-id="0692b-110">您可以只宣告 [get](../../language-reference/keywords/get.md) 存取子，讓屬性在該型別建構函式外的任何位置皆為固定。</span><span class="sxs-lookup"><span data-stu-id="0692b-110">You can declare only the [get](../../language-reference/keywords/get.md) accessor, which makes the property immutable everywhere except in the type’s constructor.</span></span>

## <a name="example"></a><span data-ttu-id="0692b-111">範例</span><span class="sxs-lookup"><span data-stu-id="0692b-111">Example</span></span>

<span data-ttu-id="0692b-112">下列範例顯示兩個方式來實作不可變的類別，該類別具有自動實作屬性。</span><span class="sxs-lookup"><span data-stu-id="0692b-112">The following example shows two ways to implement an immutable class that has auto-implemented properties.</span></span> <span data-ttu-id="0692b-113">每一種方法會宣告具有私用 `set` 的其中一個屬性，以及僅具有 `get` 的其中一個屬性。</span><span class="sxs-lookup"><span data-stu-id="0692b-113">Each way declares one of the properties with a private `set` and one of the properties with a `get` only.</span></span>  <span data-ttu-id="0692b-114">第一個類別僅使用建構函式來初始化屬性，第二個類別使用會呼叫建構函式的靜態 Factory 方法。</span><span class="sxs-lookup"><span data-stu-id="0692b-114">The first class uses a constructor only to initialize the properties, and the second class uses a static factory method that calls a constructor.</span></span>

```csharp
// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// constructor to initialize its properties.
class Contact
{
    // Read-only properties.
    public string Name { get; }
    public string Address { get; private set; }

    // Public constructor.
    public Contact(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }
}

// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// static method and private constructor to initialize its properties.
public class Contact2
{
    // Read-only properties.
    public string Name { get; private set; }
    public string Address { get; }

    // Private constructor.
    private Contact2(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }

    // Public factory method.
    public static Contact2 CreateContact(string name, string address)
    {
        return new Contact2(name, address);
    }
}

public class Program
{
    static void Main()
    {
        // Some simple data sources.
        string[] names = {"Terry Adams","Fadi Fakhouri", "Hanying Feng",
                            "Cesar Garcia", "Debra Garcia"};
        string[] addresses = {"123 Main St.", "345 Cypress Ave.", "678 1st Ave",
                                "12 108th St.", "89 E. 42nd St."};

        // Simple query to demonstrate object creation in select clause.
        // Create Contact objects by using a constructor.
        var query1 = from i in Enumerable.Range(0, 5)
                    select new Contact(names[i], addresses[i]);

        // List elements cannot be modified by client code.
        var list = query1.ToList();
        foreach (var contact in list)
        {
            Console.WriteLine("{0}, {1}", contact.Name, contact.Address);
        }

        // Create Contact2 objects by using a static factory method.
        var query2 = from i in Enumerable.Range(0, 5)
                        select Contact2.CreateContact(names[i], addresses[i]);

        // Console output is identical to query1.
        var list2 = query2.ToList();

        // List elements cannot be modified by client code.
        // CS0272:
        // list2[0].Name = "Eugene Zabokritski";

        // Keep the console open in debug mode.
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}

/* Output:
    Terry Adams, 123 Main St.
    Fadi Fakhouri, 345 Cypress Ave.
    Hanying Feng, 678 1st Ave
    Cesar Garcia, 12 108th St.
    Debra Garcia, 89 E. 42nd St.
*/
```

<span data-ttu-id="0692b-115">編譯器會針對每個自動實作屬性建立支援欄位。</span><span class="sxs-lookup"><span data-stu-id="0692b-115">The compiler creates backing fields for each auto-implemented property.</span></span> <span data-ttu-id="0692b-116">欄位不是可以直接從原始程式碼存取的。</span><span class="sxs-lookup"><span data-stu-id="0692b-116">The fields are not accessible directly from source code.</span></span>

## <a name="see-also"></a><span data-ttu-id="0692b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0692b-117">See also</span></span>

- [<span data-ttu-id="0692b-118">屬性</span><span class="sxs-lookup"><span data-stu-id="0692b-118">Properties</span></span>](./properties.md)
- [<span data-ttu-id="0692b-119">struct</span><span class="sxs-lookup"><span data-stu-id="0692b-119">struct</span></span>](../../language-reference/keywords/struct.md)
- [<span data-ttu-id="0692b-120">物件和集合初始設定式</span><span class="sxs-lookup"><span data-stu-id="0692b-120">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
