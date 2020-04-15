---
title: C# 保留屬性:追蹤呼叫者資訊
ms.date: 04/09/2020
description: 這些屬性指示編譯器生成有關調用成員的代碼的資訊。 您可以使用呼叫者檔案路徑、呼叫者行號和通話名稱提供詳細的追蹤資訊
ms.openlocfilehash: ee061d4cae35bdcc0b89007e360e94fee8c5f87c
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389874"
---
# <a name="reserved-attributes-determine-caller-information"></a>保留屬性:確定呼叫者資訊

使用資訊屬性,可以獲取有關方法調用方的資訊。 獲取原始碼的檔案路徑、原始碼中的行號和呼叫方的成員姓名。 若要取得成員呼叫端資訊，請使用套用至選擇性參數的屬性。 每個選擇性參數都會指定預設值。 下表列出 <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> 命名空間中定義的 Caller Info 屬性：

|屬性|描述|類型|
|---|---|---|
|<xref:System.Runtime.CompilerServices.CallerFilePathAttribute>|包含呼叫端的原始程式檔完整路徑。 完整路徑是編譯時的路徑。|`String`|
|<xref:System.Runtime.CompilerServices.CallerLineNumberAttribute>|原始程式檔中呼叫方法的行號。|`Integer`|
|<xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>|呼叫端的方法名稱或屬性名稱。|`String`|

此資訊可説明您編寫追蹤、除錯和創建診斷工具。 下面的範例示範如何使用調用方資訊屬性。 每次呼叫 `TraceMessage` 方法時，呼叫端資訊會替代做為選擇性參數的引數。

```csharp
public void DoProcessing()
{
    TraceMessage("Something happened.");
}

public void TraceMessage(string message,
        [CallerMemberName] string memberName = "",
        [CallerFilePath] string sourceFilePath = "",
        [CallerLineNumber] int sourceLineNumber = 0)
{
    Trace.WriteLine("message: " + message);
    Trace.WriteLine("member name: " + memberName);
    Trace.WriteLine("source file path: " + sourceFilePath);
    Trace.WriteLine("source line number: " + sourceLineNumber);
}

// Sample Output:
//  message: Something happened.
//  member name: DoProcessing
//  source file path: c:\Visual Studio Projects\CallerInfoCS\CallerInfoCS\Form1.cs
//  source line number: 31
```

為每個可選參數指定顯式預設值。 不能將調用方資訊屬性應用於未指定為可選的參數。 調用方資訊屬性不使參數成為可選參數。 而是會影響省略引數時傳入的預設值。 調用方資訊值在編譯時以文本身份發送到中間語言 (IL)。 結果不受模糊化所影響，與 <xref:System.Exception.StackTrace%2A> 屬性中例外狀況的結果不同。 您可以明確提供選擇性引數來控制呼叫端資訊，或是隱藏呼叫端資訊。

### <a name="member-names"></a>成員名稱

您可以使用 `CallerMemberName` 屬性避免指定成員名稱做為所呼叫方法的 `String` 引數。 利用這個技巧就可以避免發生 [重新命名重構]**** 未變更 `String` 值這個問題。 這項優點對於下列工作特別有用：

- 使用追蹤和診斷常式。
- 當繫結資料時，實作 <xref:System.ComponentModel.INotifyPropertyChanged> 介面。 這個介面可讓物件的屬性告知繫結的控制項屬性已變更，所以控制項可以顯示更新的資訊。 沒有 `CallerMemberName` 屬性 (Attribute)，您就必須指定屬性 (Property) 名稱做為常值。

下圖顯示當您使用 `CallerMemberName` 屬性時，傳回的成員名稱。

|呼叫發生在|成員名稱結果|
|-|-|
|方法、屬性或事件|產生呼叫的方法、屬性或事件的名稱。|
|建構函式|字串 ".ctor"|
|靜態建構函式|字串 ".cctor"|
|解構函式|字串 "Finalize"|
|使用者定義的運算子或轉換|產生的成員名稱，例如 "op_Addition"。|
|屬性建構函式|套用屬性 (attribute) 的方法或屬性 (property) 名稱。 如果屬性為成員內的任何項目 (例如參數、傳回值或泛型類型參數)，這個結果會是與該項目相關聯的成員名稱。|
|無包含的成員 (例如，組件層級或套用至類型的屬性)。|選擇性參數的預設值。|

## <a name="see-also"></a>另請參閱

- [具名和選擇性引數](../../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- <xref:System.Reflection>
- <xref:System.Attribute>
- [屬性](../../../standard/attributes/index.md)
