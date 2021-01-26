---
title: 作法：對應 HRESULT 和例外狀況
description: 請參閱如何將 COM 方法傳回的 HRESULT 值對應到 .NET 方法擲回的例外狀況。 執行時間會處理 COM 與 .NET 之間的轉換。
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- interoperation with unmanaged code, HRESULTs
- exceptions, HRESULTs
- interoperation with unmanaged code, exceptions
- HRESULTs
- COM interop, HRESULTs
- COM interop, exceptions
ms.assetid: 610b364b-2761-429d-9c4a-afbc3e66f1b9
ms.openlocfilehash: ff20dc50e1a5f1ce87a4a40691110d247b52e479
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794686"
---
# <a name="how-to-map-hresults-and-exceptions"></a>作法：對應 HRESULT 和例外狀況

COM 方法是藉由傳回 HRESULT 來報告錯誤；.NET 方法則是藉由擲回例外狀況來報告錯誤。 執行階段則負責處理兩者之間的轉換。 .NET Framework 的每一個例外狀況類別都會對應到一個 HRESULT。

 使用者定義的例外狀況類別可以指定任何適當的 HRESULT。 這些例外狀況類別可以在例外狀況物件上設定欄位時，動態變更要傳回的 HRESULT `HResult` 。 例外狀況的其他資訊是透過介面提供給用戶端 `IErrorInfo` ，該介面是在非受控進程的 .net 物件上所執行。

 如果您建立擴充的類別 `System.Exception` ，則必須在結構期間設定 HRESULT 欄位。 否則，基底類別會指派 HRESULT 值。 您可以在例外狀況的建構函式中提供值，將新的例外狀況類別對應到現有的 HRESULT。

 請注意，執行階段有時候會忽略 `HRESULT`，以應付萬一執行緒上存在 `IErrorInfo` 的情況。  如果 `HRESULT` 和 `IErrorInfo` 並不代表相同的錯誤，就可能會發生這種行為。

### <a name="to-create-a-new-exception-class-and-map-it-to-an-hresult"></a>建立新的例外狀況類別並將其對應到 HRESULT

1. 使用下列程式碼來建立稱為 `NoAccessException` 的新例外狀況類別，並將其對應到 HRESULT `E_ACCESSDENIED`。

    ```cpp
    Class NoAccessException : public ApplicationException
    {
        NoAccessException () {
        HResult = E_ACCESSDENIED;
    }
    }
    CMyClass::MethodThatThrows
    {
    throw new NoAccessException();
    }
    ```

 您也許會遇到同時使用 Managed 和 Unmanaged 程式碼的程式 (以任何程式語言所撰寫)。 例如，在下列程式碼範例中，自訂封送處理器會使用 `Marshal.ThrowExceptionForHR(int HResult)` 方法來擲回具有特定 HRESULT 值的例外狀況。 此方法會查詢 HRESULT 並產生適當的例外狀況,類型。 例如，下列程式碼片段中的 HRESULT 會產生 `ArgumentException` 。

```cpp
CMyClass::MethodThatThrows
{
    Marshal.ThrowExceptionForHR(COR_E_ARGUMENT);
}
```

 下表提供從 HRESULT 到其在 .NET 中可比較之例外狀況類別的一般對應。 不含明確對應的 HRESULT 值會對應至 `COMException` 。 完成最新的對應可以在 [dotnet/runtime 儲存](https://github.com/dotnet/runtime/blob/master/src/coreclr/vm/rexcep.h)機制中找到。

|HRESULT|.NET 例外狀況|
|-------------|--------------------|
|`COR_E_APPLICATION`|`ApplicationException`|
|`COR_E_ARGUMENT` 或 `E_INVALIDARG`|`ArgumentException`|
|`COR_E_ARGUMENTOUTOFRANGE`|`ArgumentOutOfRangeException`|
|`COR_E_ARITHMETIC or ERROR_ARITHMETIC_OVERFLOW`|`ArithmeticException`|
|`COR_E_ARRAYTYPEMISMATCH`|`ArrayTypeMismatchException`|
|`COR_E_BADIMAGEFORMAT or ERROR_BAD_FORMAT`|`BadImageFormatException`|
|`COR_E_DIRECTORYNOTFOUND or ERROR_PATH_NOT_FOUND`|`DirectoryNotFoundException`|
|`COR_E_DIVIDEBYZERO`|`DivideByZeroException`|
|`COR_E_DUPLICATEWAITOBJECT`|`DuplicateWaitObjectException`|
|`COR_E_ENDOFSTREAM`|`EndOfStreamException`|
|`COR_E_ENTRYPOINTNOTFOUND`|`EntryPointNotFoundException`|
|`COR_E_EXCEPTION`|`Exception`|
|`COR_E_EXECUTIONENGINE`|`ExecutionEngineException`|
|`COR_E_FIELDACCESS`|`FieldAccessException`|
|`COR_E_FILENOTFOUND or ERROR_FILE_NOT_FOUND`|`FileNotFoundException`|
|`COR_E_FORMAT`|`FormatException`|
|`COR_E_INDEXOUTOFRANGE`|`IndexOutOfRangeException`|
|`COR_E_INVALIDCAST or E_NOINTERFACE`|`InvalidCastException`|
|`COR_E_INVALIDFILTERCRITERIA`|`InvalidFilterCriteriaException`|
|`COR_E_INVALIDOPERATION`|`InvalidOperationException`|
|`COR_E_IO`|`IOException`|
|`COR_E_MEMBERACCESS`|`AccessException`|
|`COR_E_METHODACCESS`|`MethodAccessException`|
|`COR_E_MISSINGFIELD`|`MissingFieldException`|
|`COR_E_MISSINGMANIFESTRESOURCE`|`MissingManifestResourceException`|
|`COR_E_MISSINGMEMBER`|`MissingMemberException`|
|`COR_E_MISSINGMETHOD`|`MissingMethodException`|
|`COR_E_NOTFINITENUMBER`|`NotFiniteNumberException`|
|`E_NOTIMPL`|`NotImplementedException`|
|`COR_E_NOTSUPPORTED`|`NotSupportedException`|
|`COR_E_NULLREFERENCE orE_POINTER`|`NullReferenceException`|
|`COR_E_OUTOFMEMORY or`<br /><br /> `E_OUTOFMEMORY`|`OutOfMemoryException`|
|`COR_E_OVERFLOW`|`OverflowException`|
|`COR_E_PATHTOOLONG or ERROR_FILENAME_EXCED_RANGE`|`PathTooLongException`|
|`COR_E_RANK`|`RankException`|
|`COR_E_REFLECTIONTYPELOAD`|`ReflectionTypeLoadException`|
|`COR_E_SECURITY`|`SecurityException`|
|`COR_E_SERIALIZATION`|`SerializationException`|
|`COR_E_STACKOVERFLOW orERROR_STACK_OVERFLOW`|`StackOverflowException`|
|`COR_E_SYNCHRONIZATIONLOCK`|`SynchronizationLockException`|
|`COR_E_SYSTEM`|`SystemException`|
|`COR_E_TARGET`|`TargetException`|
|`COR_E_TARGETINVOCATION`|`TargetInvocationException`|
|`COR_E_TARGETPARAMCOUNT`|`TargetParameterCountException`|
|`COR_E_THREADINTERRUPTED`|`ThreadInterruptedException`|
|`COR_E_THREADSTATE`|`ThreadStateException`|
|`COR_E_TYPELOAD`|`TypeLoadException`|
|`COR_E_TYPEINITIALIZATION`|`TypeInitializationException`|
|`COR_E_VERIFICATION`|`VerificationException`|

 若要擷取擴充錯誤資訊，Managed 用戶端必須檢查所產生之例外狀況物件的欄位。 若要讓例外狀況物件提供有關錯誤的實用資訊，COM 物件必須執行 `IErrorInfo` 介面。 執行時間會使用提供的資訊 `IErrorInfo` 來初始化例外狀況物件。

 如果 COM 物件不支援 `IErrorInfo` ，則執行時間會使用預設值來初始化例外狀況物件。 下表列出與例外狀況物件相關聯的每個欄位，並在 COM 物件支援時，識別預設資訊的來源 `IErrorInfo` 。

 請注意，執行階段有時候會忽略 `HRESULT`，以應付萬一執行緒上存在 `IErrorInfo` 的情況。  如果 `HRESULT` 和 `IErrorInfo` 並不代表相同的錯誤，就可能會發生這種行為。

|例外狀況欄位|來自 COM 的資訊來源|
|---------------------|------------------------------------|
|`ErrorCode`|從呼叫傳回的 HRESULT。|
|`HelpLink`|如果 `IErrorInfo->HelpContext` 是非零值，則字串會藉由串連 `IErrorInfo->GetHelpFile` 和 "#" 和來形成 `IErrorInfo->GetHelpContext` 。 否則會從傳回字串 `IErrorInfo->GetHelpFile` 。|
|`InnerException`|在 Visual Basic) 中，一律為 null 參考 (`Nothing` 。|
|`Message`|從傳回的字串 `IErrorInfo->GetDescription` 。|
|`Source`|從傳回的字串 `IErrorInfo->GetSource` 。|
|`StackTrace`|堆疊追蹤。|
|`TargetSite`|傳回失敗 HRESULT 之方法的名稱。|

 例外狀況欄位（例如 `Message` 、 `Source` 和） `StackTrace` 無法供使用 `StackOverflowException` 。

## <a name="see-also"></a>另請參閱

- [進階 COM 互通性](/previous-versions/dotnet/netframework-4.0/bd9cdfyx(v=vs.100))
- [例外狀況](../../standard/exceptions/index.md)
