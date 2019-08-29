---
title: 呼叫端資訊
description: 描述如何使用呼叫端資訊引數屬性, 從方法取得呼叫端資訊。
ms.date: 04/25/2017
ms.openlocfilehash: e7bbc3830a95bd25cfc2fb369b204d367b775815
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106588"
---
# <a name="caller-information"></a>呼叫端資訊

使用 Caller Info 屬性，您就可以取得有關方法之呼叫端的資訊。 您可以取得原始程式碼的檔案路徑、原始程式碼中的行號，以及呼叫端的成員名稱。 這項資訊有助於追蹤、偵錯及建立診斷工具。

若要取得這項資訊，可使用套用至選擇性參數的屬性，每個屬性都有預設值。 下表列出在[CompilerServices](/dotnet/api/system.runtime.compilerservices)命名空間中定義的呼叫端資訊屬性:

|屬性|描述|類型|
|---------|-----------|----|
|[CallerFilePath](/dotnet/api/system.runtime.compilerservices.callerfilepathattribute)|包含呼叫端的原始程式檔完整路徑。 這是編譯時間的檔案路徑。|`String`
|[CallerLineNumber](/dotnet/api/system.runtime.compilerservices.callerlinenumberattribute)|原始程式檔中呼叫方法所在的行號。|`Integer`|
|[CallerMemberName](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)|呼叫端的方法或屬性名稱。 請參閱本主題稍後的成員名稱一節。|`String`|

## <a name="example"></a>範例

下列範例會示範如何使用這些屬性來追蹤呼叫端。

```fsharp
open System.Diagnostics
open System.Runtime.CompilerServices
open System.Runtime.InteropServices

type Tracer() =
    member __.DoTrace(message: string,
                      [<CallerMemberName; Optional; DefaultParameterValue("")>] memberName: string,
                      [<CallerFilePath; Optional; DefaultParameterValue("")>] path: string,
                      [<CallerLineNumber; Optional; DefaultParameterValue(0)>] line: int) =
        Trace.WriteLine(sprintf "Message: %s" message)
        Trace.WriteLine(sprintf "Member name: %s" memberName)
        Trace.WriteLine(sprintf "Source file path: %s" path)
        Trace.WriteLine(sprintf "Source line number: %d" line)
```

## <a name="remarks"></a>備註

呼叫端資訊屬性只能套用至選擇性參數。 呼叫端資訊屬性會使編譯器為每個以呼叫者資訊屬性裝飾的選擇性參數寫入適當的值。

在編譯時期，Caller Info 的值會做為常值發出至中繼語言 (IL)。 不同于例外狀況的[StackTrace](/dotnet/api/system.diagnostics.stacktrace)屬性結果, 結果不會受到模糊處理的影響。

您可以明確提供選擇性引數來控制呼叫端資訊，或是隱藏呼叫端資訊。

## <a name="member-names"></a>成員名稱

您可以使用[`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)屬性, 避免將成員名稱指定`String`為所呼叫方法的引數。 藉由使用這項技術, 您可以避免重新命名重構不會`String`變更值的問題。 這項優點對於下列工作特別有用：

- 使用追蹤和診斷常式。
- 系結資料時, 執行[INotifyPropertyChanged](/dotnet/api/system.componentmodel.inotifypropertychanged)介面。 這個介面可讓物件的屬性告知繫結的控制項屬性已變更，所以控制項可以顯示更新的資訊。 如果沒有[`CallerMemberName`](/dotnet/api/system.runtime.compilerservices.callermembernameattribute)屬性, 您必須將屬性名稱指定為常值。

下圖顯示當您使用 CallerMemberName 屬性時, 所傳回的成員名稱。

|呼叫發生於|成員名稱結果|
|-------------------|------------------|
|方法、屬性或事件|產生呼叫的方法、屬性或事件的名稱。|
|建構函式|字串 ".ctor"|
|靜態建構函式|字串 ".cctor"|
|解構函式|字串 "Finalize"|
|使用者定義的運算子或轉換|產生的成員名稱，例如 "op_Addition"。|
|屬性建構函式|套用屬性的成員名稱。 如果屬性為成員內的任何項目 (例如參數、傳回值或泛型類型參數)，這個結果會是與該項目相關聯的成員名稱。|
|無包含的成員 (例如，組件層級或套用至類型的屬性)。|選擇性參數的預設值。|

## <a name="see-also"></a>另請參閱

- [屬性](attributes.md)
- [具名引數](parameters-and-arguments.md#named-arguments)
- [選擇性參數](parameters-and-arguments.md#optional-parameters)
