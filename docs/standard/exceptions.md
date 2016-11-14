---
title: "在 .NET 中處理和擲回例外狀況"
description: "了解如何在 .NET 中使用例外狀況"
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bf116df6-0042-46bf-be13-b69864816210
translationtype: Human Translation
ms.sourcegitcommit: 9584699ad7e745ae3cb059b1bb8327301c9a3286
ms.openlocfilehash: 0c73fb0a12092877ff5b54221f4a80693d1d1152

---

# <a name="handling-and-throwing-exceptions-in-net"></a>在 .NET 中處理和擲回例外狀況

應用程式必須能以一致的方式處理執行期間發生的錯誤。 .NET 提供模型，可以統一的方式通知應用程式的錯誤：.NET 作業會藉由擲回例外狀況指出失敗。

## <a name="exceptions"></a>例外狀況

例外狀況是執行程式所遇到的錯誤狀況或未預期的行為。 若是程式碼或您呼叫的程式碼 (例如共用程式庫) 中有錯誤、無法使用作業系統資源、執行階段遇到非預期的狀況 (例如無法驗證的程式碼) 等等，就可能擲回例外狀況。 您的應用程式可從一些狀況中復原，但有些狀況就無法復原。 雖然您可以從應用程式的大部分例外狀況中復原，但卻無法從執行階段的大部分例外狀況中復原。

在 .NET 中，例外狀況是從 [System.Exception](xref:System.Exception) 類別繼承的物件。 從發生問題的程式碼區域擲回例外狀況。 例外狀況會向上傳遞堆疊，直到應用程式處理或程式終止它。

## <a name="exceptions-vs-traditional-errorhandling-methods"></a>例外狀況與傳統錯誤處理方法的比較

傳統上，一種語言的錯誤處理模型不是依賴語言唯一偵測錯誤的方式與尋找處理常式，就是依賴作業系統所提供的錯誤處理機制。 .NET 實作例外狀況處理的方式具有下列優點：

- .NET 程式語言擲回和處理例外狀況的方式都相同。

- 要處理例外狀況不需要任何特定語言的語法，但可讓每一種語言定義自己的語法。

- 例外狀況可跨處理序，甚至是跨電腦界限擲回。

- 可將例外狀況處理程式碼加入應用程式，以增加程式可靠性。

例外狀況優於其他錯誤通知方法，例如傳回碼。 不會發生未通知失敗的情況，因為如果擲回例外狀況而您未加以處理，執行階段就會終止您的應用程式。 也不會因為程式碼無法檢查失敗傳回碼，就繼續在整個系統散佈無效的值。 

## <a name="exception-class-and-properties"></a>Exception 類別和屬性

@System.Exception 類別是例外狀況所繼承的基底類別。 例如 @System.InvalidCastException 類別的階層如下：

```
Object
  Exception
    SystemException
       InvalidCastException
```

@System.Exception 類別具有下列屬性，讓您更容易了解例外狀況。

| 屬性名稱 | 說明 |
| ------------- | ----------- |
| @System.Exception.Data | @System.Collections.IDictionary 會將任意資料保存在索引鍵/值組。 |
| @System.Exception.HelpLink | 可保留說明檔的 URL (或 URN)，以提供有關例外狀況原因的廣泛資訊。 |
| @System.Exception.InnerException | 您可以在例外狀況處理期間，使用此屬性來建立及保留一系列的例外狀況。 您可以使用此屬性來建立新的例外狀況，其中包含先前攔截例外狀況。 @System.Exception.InnerException 屬性中的第二個例外狀況可以擷取原始的例外狀況，讓程式碼可以處理第二個例外狀況，以檢視其他額外的資訊。 例如，假設您有一個方法會接收格式不正確的引數。  此程式碼會嘗試讀取引數，但擲回例外狀況。 此方法會攔截例外狀況，並擲回 @System.FormatException.。為改善呼叫端判斷例外狀況擲回原因的能力，有時會需要方法攔截協助程式常式擲回的例外狀況，然後再擲回例外狀況更清楚地指出所發生的錯誤。 您可以建立全新且更有意義的例外狀況，其中的內部例外狀況參考可設定為原始例外狀況。 這個更有意義的例外狀況接著會擲回給呼叫端。 請注意，透過這項功能，您可以建立一系列的連結例外狀況，每個例外狀況後面接著先前擲回的例外狀況。 |
| @System.Exception.Message | 提供有關例外狀況原因的詳細資料。
| @System.Exception.Source | 取得或設定造成錯誤的應用程式或物件的名稱。 |
| @System.Exception.StackTrace | 包含可用來判斷發生錯誤位置的堆疊追蹤。 堆疊追蹤包括原始程式檔名稱和程式行號 (若有偵錯資訊的話)。 |

大部分繼承自 @System.Exception 的類別都不會實作其他成員，也不會提供其他功能，而只會繼承 @System.Exception.。因此可以在例外狀況類別階層、例外狀況名稱及例外狀況內含的資訊中，找到例外狀況最重要的資訊。

建議只擲回及攔截衍生自 @System.Exception, 的物件，但您可以擲回任何衍生自 @System.Object 類別的物件作為例外狀況。 請注意，並非所有語言都能擲回及攔截不是衍生自 @System.Exception. 的物件。

## <a name="common-exceptions"></a>常見的例外狀況

下表列出一些常見的例外狀況，並提供可能造成這些例外狀況的原因範例。

| 例外狀況類型 | 基底類型 | 描述 | 範例 |
| -------------- | --------- | ----------- | ------- |
| @System.Exception | @System.Object | 適用於所有例外狀況的基底類別。 | 無 (使用這個例外狀況的衍生類別)。 |
| @System.IndexOutOfRangeException | @System.Exception | 只有當陣列索引不正確時，才由執行階段擲回。 | 在有效的陣列範圍之外編製陣列索引：`arr[arr.Length+1]` |
| @System.NullReferenceException | @System.Exception | 只有當參考 Null 物件時，才由執行階段擲回。 | `object o = null; o.ToString();` |
| @System.InvalidOperationException | @System.Exception | 當處於無效狀態時，由方法擲回。 | 在從基礎集合將 Item 移除之後，呼叫 `Enumerator.GetNext()`。 |
| @System.ArgumentException | @System.Exception | 適用於所有引數例外狀況的基底類別。 | 無 (使用這個例外狀況的衍生類別)。 |
| @System.ArgumentNullException | @System.Exception | 由不允許引數為 Null 的方法擲回。 | `String s = null; "Calculate".IndexOf (s);` |
| @System.ArgumentOutOfRangeException | @System.Exception | 由驗證引數是在指定範圍內的方法擲回。 | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>如何使用 try/catch 區塊攔截例外狀況

將可能擲回例外狀況的程式碼區段放在 `try` 區塊中，並將處理例外狀況的程式碼放在 `catch` 區塊中。 `catch` 區塊為一系列的陳述式，以關鍵字 `catch` 開頭，後面接著例外狀況類型和要採取的動作。

下列程式碼範例使用 `try`/`catch` 區塊攔截可能的例外狀況。 `Main` 方法包含內存 @System.IO.StreamReader 陳述式的 `try` 區塊，該陳述式可開啟名為 `data.txt` 的資料檔案，並寫入檔案中的字串。 `try` 區塊後面接著 `catch` 區塊，該區塊會攔截 `try` 區塊所產生的任何例外狀況。

C#
```
using System;
using System.IO;

public class ProcessFile
{
    public static void Main()
    {
        try
        {
            StreamReader sr = File.OpenText("data.txt");
            Console.WriteLine("The first line of this file is {0}", sr.ReadLine());
            sr.Dispose();
        }
        catch (Exception e)
        {
            Console.WriteLine("An error occurred: '{0}'", e);
        }
    }
}
```

Common Language Runtime 會攔截 catch 區塊未攔截的例外狀況。 根據執行階段的設定方式，可能會發生下列其中一種情況：顯示偵錯對話方塊、程式停止執行並顯示內含例外狀況資訊的對話方塊，或錯誤印出至 STDERR。

> [!NOTE] 
> 幾乎所有程式碼行都能引發例外狀況，特別是 Common Language Runtime 本身擲回的例外狀況，例如 @System.OutOfMemoryException.。大部分應用程式無須處理這些例外狀況，但在撰寫供他人使用的程式庫，應留意此可能性。 如需何時在 Try 區塊中設定程式碼的建議，請參閱[例外狀況的最佳做法](#best-practices-for-exceptions)。
 
## <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>如何使用 Catch 區塊中的特定例外狀況

上述程式碼範例示範攔截任何例外狀況的基本 `catch` 陳述式。 一般而言，比起使用基本 `catch` 陳述式，攔截特定例外狀況類型會是更佳的程式設計做法。

發生例外狀況時，該例外狀況會在堆疊中向上傳遞，讓每個 catch 區塊都有機會處理。 Catch 陳述式的順序很重要。 請將針對特定例外狀況的 catch 區塊放在一般例外狀況的 catch 區塊之前，否則編譯器可能會發出錯誤。 藉由比對 catch 區塊中指定的例外狀況類型與例外狀況名稱，即可決定正確的 catch 區塊。 如果沒有特定 catch 區塊，則會由一般 catch 區塊 (如果有的話) 攔截例外狀況。

下列程式碼範例使用 `try`/`catch` 區塊攔截 @System.InvalidCastException.。此範例會建立名為的類別 `Employee` 並只具有員工層級一個屬性 (`Emlevel`) 的類別。 `PromoteEmployee` 方法會採用一個物件並遞增員工層級。 @System.InvalidCastException 會在 @System.DateTime 執行個體傳遞給 `PromoteEmployee` 方法時發生。

C#
```
using System;

public class Employee
{
    //Create employee level property.
    public int Emlevel
    {
        get
        {
            return(emlevel);
        }
        set
        {
            emlevel = value;
        }
    }

    private int emlevel = 0;
}

public class Ex13
{
    public static void PromoteEmployee(Object emp)
    {
        //Cast object to Employee.
        Employee e = (Employee) emp;
        // Increment employee level.
        e.Emlevel = e.Emlevel + 1;
    }

    public static void Main()
    {
        try
        {
            Object o = new Employee();
            DateTime newyears = new DateTime(2001, 1, 1);
            //Promote the new employee.
            PromoteEmployee(o);
            //Promote DateTime; results in InvalidCastException as newyears is not an employee instance.
            PromoteEmployee(newyears);
        }
        catch (InvalidCastException e)
        {
            Console.WriteLine("Error passing data to PromoteEmployee method. " + e.Message);
        }
    }
}
```

## <a name="how-to-use-finally-blocks"></a>如何使用 finally 區塊

發生例外狀況時，執行會停止，並將控制權交給適當的例外狀況處理常式。 這通常表示會略過您預期要執行的程式碼行。 某些資源清除作業 (例如關閉檔案) 即使擲回例外狀況也必須執行。 若要這樣做，您可以使用 `finally` 區塊。 `finally` 區塊永遠會執行，而不論是否擲回例外狀況。

下列程式碼範例使用 `try`/`catch` 區塊攔截 @System.ArgumentOutOfRangeException.。`Main` 方法會建立兩個陣列，並嘗試從其中一個複製到另一個。 此動作會產生 @System.ArgumentOutOfRangeException，並會將錯誤寫入主控台。 不論複製動作的結果為何，`finally` 區塊都會執行。

C#
```
using System;

class ArgumentOutOfRangeExample
{
    public static void Main()
    {
        int[] array1 = {0, 0};
        int[] array2 = {0, 0};

        try
        {
            Array.Copy(array1, array2, -1);
        }
        catch (ArgumentOutOfRangeException e)
        {
            Console.WriteLine("Error: {0}", e);
        }
        finally
        {
            Console.WriteLine("This statement is always executed.");
        }
    }
}
```

## <a name="how-to-explicitly-throw-exceptions"></a>如何明確擲回例外狀況

您可以使用 `throw` 陳述式，明確擲回例外狀況。 您也可以使用 `throw` 陳述式，再次擲回所攔截的例外狀況。 建議您撰寫程式碼，將資訊加入要重新擲回的例外狀況，以在偵錯時提供更多資訊。

下列程式碼範例使用 `try`/`catch` 區塊攔截可能的 @System.IO.FileNotFoundException.。下列 `try` 區塊是 `catch` 區塊，會攔截 @System.IO.FileNotFoundException，並會在找不到資料檔案時，寫入一則訊息到主控台。 下一個陳述式是 `throw` 陳述式，會擲回新的 @System.IO.FileNotFoundException ，並將文字資訊新增到例外狀況。

C#
```
using System;
using System.IO;

public class ProcessFile
{
   public static void Main()
      {
      FileStream fs = null;
      try   
      {
         //Opens a text tile.
         fs = new FileStream(@"C:\temp\data.txt", FileMode.Open);
         StreamReader sr = new StreamReader(fs);
         string line;

         //A value is read from the file and output to the console.
         line = sr.ReadLine();
         Console.WriteLine(line);
      }
      catch(FileNotFoundException e)
      {
         Console.WriteLine("[Data File Missing] {0}", e);
         throw new FileNotFoundException(@"[data.txt not in c:\temp directory]",e);
      }
      finally
      {
         if (fs != null)
            fs.Dispose();
      }
   }
}
```

## <a name="how-to-create-userdefined-exceptions"></a>如何建立使用者定義的例外狀況

.NET 提供的例外狀況類別階層最終由基底類別 @System.Exception. 衍生而出。倘若沒有任何預先定義的例外狀況符合您的需求，您可以從 @System.Exception衍生建立您自己的例外狀況類別。

建立您自己的例外狀況時，以文字 "Exception" 作為使用者定義例外狀況類別名稱的結尾，並實作三種常見的建構函式，如下列範例所示。 此範例會定義名為 `EmployeeListNotFoundException` 的新例外狀況類別。 此類別衍生自 @System.Exception，包含三個建構函式。

C#
```
using System;

public class EmployeeListNotFoundException: Exception
{
    public EmployeeListNotFoundException()
    {
    }

    public EmployeeListNotFoundException(string message)
        : base(message)
    {
    }

    public EmployeeListNotFoundException(string message, Exception inner)
        : base(message, inner)
    {
    }
}
```

> [!NOTE]
> 在您使用遠端功能的情況下，您必須確定任何使用者定義例外狀況的中繼資料是由伺服器 (被呼叫端) 提供，並提供給用戶端 (Proxy 物件或呼叫端)。 如需詳細資訊，請參閱[例外狀況的最佳做法](#best-practices-for-exceptions)。

## <a name="best-practices-for-exceptions"></a>例外狀況的最佳做法

設計良好的應用程式可處理例外狀況和錯誤，防止應用程式損毀。 本節說明處理和建立例外狀況的最佳做法。

### <a name="use-trycatchfinally-blocks"></a>使用 try/catch/finally 區塊

使用 `try`/`catch`/`finally` 區塊括住程式碼可能會產生例外狀況。 

在 `catch` 區塊中，一律將例外狀況從最特殊的排列到最不特殊的。

不論您是否可以復原，使用 `finally` 區塊都可清除資源。

### <a name="handle-common-conditions-without-throwing-exceptions"></a>處理常見的狀況，而不擲回例外狀況

針對可能發生但可能會觸發例外狀況的狀況，請考慮以避免例外狀況的方式來處理這些狀況。 例如，如果您嘗試關閉已關閉的連線，您會得到 `InvalidOperationException`。 您可以在嘗試關閉之前，使用 `if` 陳述式來檢查連線狀態，以避免此例外狀況。

C#
```
if (conn.State != ConnectionState.Closed)
{
    conn.Close();
}
```

如果您沒有檢查連線狀態就關閉，您可能會攔截到 `InvalidOperationException` 例外狀況。

C#
```
try
{
    conn.Close();
}
catch (InvalidOperationException ex)
{
    Console.WriteLine(ex.GetType().FullName);
    Console.WriteLine(ex.Message);
}
```

選擇的方法取決於您預期事件會發生的頻率。

- 如果事件不常發生，也就是說事件真的是例外並且表示錯誤 (例如未預期的檔案結尾)，則使用例外狀況處理。 當您使用例外狀況處理時，在正常情況下會執行較少的程式碼。

- 如果事件定期發生而且可視為正常執行的一部分，請檢查程式碼中是否有錯誤狀況。 當您檢查是否有常見的錯誤狀況時，因為避免例外狀況，所以會執行較少的程式碼。

### <a name="design-classes-so-that-exceptions-can-be-avoided"></a>設計類別以避免例外狀況

類別可提供方法或屬性，讓您避免進行會觸發例外狀況的呼叫。 例如，@System.IO.FileStream 類別會提供方法，協助判斷是否已經抵達檔案結尾。 這些方法或屬性可用來避免萬一您讀取超過檔案結尾時，所擲回的例外狀況。 下列範例示範如何讀取至檔案結尾，而不會觸發例外狀況。

C#
```
class FileRead
{
    public void ReadAll(FileStream fileToRead)
    {
        // This if statement is optional
        // as it is very unlikely that
        // the stream would ever be null.
        if (fileToRead == null)
        {
            throw new System.ArgumentNullException();
        }

        int b;

        // Set the stream position to the beginning of the file.
        fileToRead.Seek(0, SeekOrigin.Begin);

        // Read each byte to the end of the file.
        for (int i = 0; i < fileToRead.Length; i++)
        {
            b = fileToRead.ReadByte();
            Console.Write(b.ToString());
            // Or do something else with the byte.
        }
    }
}
```

另一個避免例外狀況的方法是針對很常見的錯誤案例傳回 null，而不擲回例外狀況。 相當普遍的錯誤案例可視為一般控制流程。 針對這些案例傳回 null，就能盡量降低對應用程式效能的影響。

### <a name="throw-exceptions-instead-of-returning-an-error-code"></a>擲回例外狀況來代替傳回錯誤碼

例外狀況可確保不會發生未通知失敗的情況，因為呼叫程式碼並不會檢查傳回碼。 

### <a name="use-the-predefined-net-exception-types"></a>使用預先定義的 .NET 例外狀況類型

只有在預先定義的類型不適用時，才引進新的例外狀況類別。 例如：

- 如果屬性集或方法呼叫對於物件的目前狀態而言並不適當，就會擲回 @System.InvalidOperationException 例外狀況。

- 在傳遞的參數無效時擲回 @System.ArgumentException 例外狀況，或擲回預先定義之類別中，從 @System.ArgumentException 衍生而來的類別。

### <a name="end-exception-class-names-with-the-word-exception"></a>使用字組 `Exception` 作為例外狀況類別名稱的結尾

如需自訂例外狀況，請適當地加以命名，並從 @System.Exception加以衍生。 例如：

C#
```
public class MyFileNotFoundException : Exception
{
}
```

### <a name="include-three-constructors-in-custom-exception-classes"></a>在自訂例外狀況類別中包含三個建構函式

當您建立自己的例外狀況類別時，請使用至少三個種常見的建構函式：預設建構函式、採用字串訊息的建構函式，以及採用字串訊息和內部例外狀況的建構函式。

- @System.Exception.%23ctor,，會使用預設值。

- @System.Exception.%23ctor(System.String),，會接受字串訊息。

- @System.Exception.%23ctor(System.String,System.Exception),，會接受字串訊息及內部例外狀況。

如需範例，請參閱[如何：建立使用者定義的例外狀況](#how-to-create-user-defined-exceptions)。

### <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>確保從遠端執行程式碼時可以使用例外狀況資料

當您建立使用者定義的例外狀況時，請確保例外狀況的中繼資料可供遠端執行的程式碼使用。 

例如，在實作應用程式定義域的 .NET 執行階段上，例外狀況可能會跨應用程式定義域發生。 假定應用程式定義域 A 建立應用程式定義域 B，它會執行擲回例外狀況的程式碼。 為使應用程式定義域 A 能夠正確地攔截及處理例外狀況，其必須能夠尋找含有應用程式定義域 B 所擲回之例外狀況的組件。若應用程式定義域 B 擲回例外狀況，但此例外狀況包含在位於其應用程式基底之下的組件，而不是位於在應用程式定義域 A 的應用程式基底之下的組件，應用程式定義域 A 將無法尋找例外狀況，而且 Common Language Runtime 將會擲回 @System.IO.FileNotFoundException 例外狀況。 若要避免這個情形，您可以透過兩種方式部署含有例外狀況資訊的組件：

- 將組件放入這兩個應用程式定義域共用的通用應用程式基底。

    \-或-

- 如果定義域不共用通用應用程式基底，則以強式名稱簽署含有例外狀況資訊的組件，並將組件部署到全域組件快取中。

### <a name="include-a-localized-description-string-in-every-exception"></a>在每一個例外狀況中包含當地語系化的描述字串

使用者看到的錯誤訊息是衍生自擲回的例外狀況描述字串，而不是衍生自例外狀況類別名稱。

### <a name="use-grammatically-correct-error-messages"></a>使用文法正確的錯誤訊息

撰寫清楚的句子並包含結尾標點符號。 例外狀況說明字串中的每一句應該以句號結束。 例如，「記錄資料表已溢位」 就是適當的描述字串。

### <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>在自訂例外狀況中，視需要提供額外的屬性

只有在額外資訊對某個程式設計案例有用時，才提供例外狀況的額外屬性 (以及描述字串)。 例如，@System.IO.FileNotFoundException 提供 @System.IO.FileNotFoundException.FileName 屬性。

### <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>放置 throw 陳述式讓堆疊追蹤更有用

堆疊追蹤會從擲回例外狀況所在的陳述式開始，並在攔截例外狀況的 `catch` 陳述式結束。

### <a name="use-exception-builder-methods"></a>使用例外狀況產生器方法

類別在它的實作中從不同的地方擲回相同的例外狀況是很常見的。 若要避免過多的程式碼，請使用 Helper 方法，以建立例外狀況並將它傳回。 例如: 

C#
```
class FileReader
{
    private string fileName;

    public FileReader(string path)
    {
        fileName = path;
    }

    public byte[] Read(int bytes)
    {
        byte[] results = FileUtils.ReadFromFile(fileName, bytes);
        if (results == null)
        {
            throw NewFileIOException();
        }
        return results;
    }

    FileReaderException NewFileIOException()
    {
        string description = "My NewFileIOException Description";

        return new FileReaderException(description);
    }
}

```

在某些情況下，使用例外狀況的建構函式來建置例外狀況會更適當。 範例為全域例外狀況類別 @System.ArgumentException, 

### <a name="clean-up-intermediate-results-when-throwing-an-exception"></a>在擲回例外狀況時清除中繼結果

呼叫端應該能夠假設，從方法擲回例外狀況時不會產生副作用。 例如，如果您有用來轉帳的程式碼，會從某個帳戶提款再存入另一個帳戶，而且在執行存款時擲回例外狀況，則您不想要讓提款仍有效。

C#
```
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

處理這種情況的一個方式是攔截存款交易所擲回的任何例外狀況，並復原提款。

C#
```
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw
    }
}
```

此範例說明如何使用 `throw` 重新擲回原始的例外狀況，以方便呼叫端無須檢視 @System.Exception.InnerException屬性，就能輕鬆查看問題的實際原因。 另一種做法是擲回新的例外狀況，並包含原始例外狀況作為內部例外狀況：

C#
```
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a>請參閱

若要深入了解 .NET 中例外狀況的運作方式，請參閱 [What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md)。



<!--HONumber=Nov16_HO1-->


