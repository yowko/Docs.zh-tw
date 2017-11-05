# C# 7.1 中的新增功能

在 C# 7.1 ，提供以下功能：

* [`async` 非同步方法 ( `async` `Main` method )](#async-main)
  - The entry point for an application can have the `async` modifier.
* [`default` 字元正則表達式 ( `default` literal expressions )](#default-literal-expressions)
  - You can use default literal expressions in default value expressions when the target type can be inferred.
* [推導 Tuple 型別節點 ( Inferred tuple element names )](#inferred-tuple-element-names)
  - The names of tuple elements can be inferred from tuple initialization in many cases.

## 深入瞭解新版本
C# 7.1 自 Visual Studio 2017 版本 15.3 起與 .NET Core SDK 2.0 開始支援，預設 C# 7.1 功能為關閉，
若要啟用 C# 7.1 功能，您必需確認您的專案編輯語言版本設定值。


在 Visual Studio ，設定 C# 7.1 功能啟用的方法為專案總管中欲於設定功能啟用的專案右鍵選單選擇「專案屬性」
(**Properties**) ，選擇「建置」頁籤 (**Build**) 後，按下「進階」按紐 (**Advanced**) ，將看見下面對話視窗：



在此對話視窗中選擇「語言版本 (**Build**) 選項下拉選單值為「 C# 最新主要版本」 (**C# latest minor version (latest)**) 
或為 「 C# 7.1 」(**C# 7.1**)，按下確定按紐後， Visual Studio 將會為您選取的專案 csproj 設定檔中寫入以下設定：


```xml
<PropertyGroup>
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```


選單值「 C# 最新主要版本」與「 C# 7.1 」差異在於選擇 C# 最新主要版本設定時將會使用您當前機器上的最新版本，而選擇
 「C# 7.1」 則為明確指定使用 C# 7.1 而非使用當前機器現有更新版本。

> [!註記]
> 如果使用 Visual Studio IDE 介面更新 csproj 設定檔， IDE 介面將會為您所選取專案進行個別設定更新，並產
> 生單一的設定值。然而若有為個別開發環境設定環境變數，或者在當前定選擇所有設定更新時，您將會看到以下設定方式

```xml
<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>

<PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|AnyCPU'">
  <LangVersion>latest</LangVersion>
</PropertyGroup>
```

LangVersion 提供了以下有效數值設定選項：

* `ISO-1`
* `ISO-2`
* `3`
* `4`
* `5`
* `6`
* `7`
* `7.1`
* `default`
* `latest`

文字字串 `default` 與 `latest` 分別提供使用當前機器所使用的最新版本與次要最新版本。
您可以使用最新版本 SDK 與其相關工具進行細部個別設定。


## Async 非同步方法 (Async main)

An *async main* method enables you to use `await` in your `Main` method.
Previously you would need to write:

```csharp
static int Main()
{
    return DoAsyncWork().GetAwaiter().GetResult();
}
```

You can now write:

```csharp
static async Task<int> Main()
{
    // This could also be replaced with the body
    // DoAsyncWork, including its await expressions:
    return await DoAsyncWork();
}
```

If your program doesn't return an exit code, you can declare a `Main` method
that returns a <xref:System.Threading.Tasks.Task>:

```csharp
static async Task Main()
{
    await SomeAsyncMethod();
}
```

You can read more about the details in the
[async main](../programming-guide/main-and-command-args/index.md) topic
in the programming guide.

## Default 字元正則表達式 (Default literal expressions)

Default literal expressions are an enhancement to default value expressions.
These expressions initialize a variable to the default value. Where you previously
would write:

```csharp
Func<string, bool> whereClause = default(Func<string, bool>);
```

You can now omit the type on the right-hand side of the initialization:

```csharp
Func<string, bool> whereClause = default;
```

You can learn more about this enhancement in the C# Programming Guide topic
on [default value expressions](../programming-guide/statements-expressions-operators/default-value-expressions.md).

This enhancement also changes some of the parsing rules for the [default keyword](../language-reference/keywords/default.md).

## 推導 Tuple 型別節點 (Inferred tuple element names)

This feature is a small enhancement to the tuples feature introduced in
C# 7.0. Many times when you initialize a tuple, the variables used for the
right side of the assignment are the same as the names you'd like for the
tuple elements:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count: count, label: label);
```

The names of tuple elements can be inferred from the variables used to initialize
the tuple in C# 7.1:

```csharp
int count = 5;
string label = "Colors used in the map";
var pair = (count, label); // element names are "count" and "label"
```

You can learn more about this feature in the [Tuples](../tuples.md) topic.

## 組件版本資源

There are two new compiler options that generate *reference-only assemblies*:
[/refout](../language-reference/compiler-options/refout-compiler-option.md)
and [/refonly](../language-reference/compiler-options/refonly-compiler-option.md).
The linked topics explain these options and reference assemblies in more detail.
