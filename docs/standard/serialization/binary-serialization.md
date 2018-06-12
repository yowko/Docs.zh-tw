---
title: 二進位序列化
ms.date: 01/02/2018
helpviewer_keywords:
- binary serialization
- serialization, about serialization
- deserialization
- binary serialization, about serialization
- binary serialization, .net core serialization
- serialization, cross-framework
ms.assetid: 2b1ea3be-1152-4032-b2b3-07794054c405
author: ViktorHofer
ms.author: mairaw
ms.openlocfilehash: 63158dd2dda5388870d3d5878fe29cb004aec401
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="binary-serialization"></a>二進位序列化

可定義序列化為儲存物件狀態至儲存媒體的程序。 在此程序中，物件的公用與私用欄位以及類別名稱 (包括含類別的組件)，會轉換為位元組資料流，然後寫入資料流當中。 當物件隨後還原序列化時，會建立與原始物件完全相同的複製品。

在物件導向環境中實作序列化機制時，您必須在使用簡易性與彈性之間進行許多取捨。 若您對程序擁有足夠的控制，該程序可大幅自動化。 例如，可能有簡單二進位序列化並不足夠的情況，或有特定的理由需決定類別中哪個欄位需序列化。 下列各節檢查 .NET 所提供的穩固序列化機制，並強調數種能讓您自訂程序以滿足需求的重要功能。

> [!NOTE]
> 如果使用不同的 .NET Framework 版本序列化及還原序列化 UTF-8 或 UTF-7 編碼的物件，則不會保留該物件的狀態。

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

因為二進位序列化的本質允許修改物件內的私用成員，因此變更其狀態，所以建議使用其他序列化架構，例如在公用 API 介面上操作的 JSON.NET。

## <a name="binary-serialization-in-net-core"></a>.NET Core 中的二進位序列化

.NET Core 支援一小部分類型的二進位序列化。 您可以在[可序列化類型區段](#serializable-types)中看到所支援的類型清單。 保證定義的這組類型可以在 .NET Framework 4.5.1 和更新版本與 .NET Core 2.0 和更新版本之間序列化。 其他 .NET 實作 (例如 Mono) 未正式予以支援，但應該也會運作。

### <a name="serializable-types"></a>可序列化類型

- <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:Microsoft.CSharp.RuntimeBinder.RuntimeBinderInternalCompilerException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.AccessViolationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.AggregateException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.AppDomainUnloadedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ApplicationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ArgumentException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ArgumentNullException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ArgumentOutOfRangeException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ArithmeticException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Array?displayProperty=nameWithType>   
- <xref:System.ArraySegment%601?displayProperty=nameWithType>   
- <xref:System.ArrayTypeMismatchException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Attribute?displayProperty=nameWithType>
- <xref:System.BadImageFormatException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Boolean?displayProperty=nameWithType>   
- <xref:System.Byte?displayProperty=nameWithType>   
- <xref:System.CannotUnloadAppDomainException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Char?displayProperty=nameWithType>   
- <xref:System.Collections.ArrayList?displayProperty=nameWithType>   
- <xref:System.Collections.BitArray?displayProperty=nameWithType>   
- <xref:System.Collections.Comparer?displayProperty=nameWithType>   
- <xref:System.Collections.DictionaryEntry?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Comparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.EqualityComparer%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.HashSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Collections.Generic.KeyValuePair%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.LinkedList%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Queue%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=nameWithType>   
- <xref:System.Collections.Generic.Stack%601?displayProperty=nameWithType>   
- <xref:System.Collections.Hashtable?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.Collection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.KeyedCollection%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602?displayProperty=nameWithType>   
- <xref:System.Collections.ObjectModel.ReadOnlyObservableCollection%601?displayProperty=nameWithType>   
- <xref:System.Collections.Queue?displayProperty=nameWithType>   
- <xref:System.Collections.SortedList?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.HybridDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.ListDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.OrderedDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringCollection?displayProperty=nameWithType>   
- <xref:System.Collections.Specialized.StringDictionary?displayProperty=nameWithType>   
- <xref:System.Collections.Stack?displayProperty=nameWithType>   
- `System.Collections.Generic.NonRandomizedStringEqualityComparer` <!--zz <xref:System.Collections.Generic.NonRandomizedStringEqualityComparer?displayProperty=nameWithType> --> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ComponentModel.BindingList%601?displayProperty=nameWithType>   
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ComponentModel.Design.CheckoutException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ComponentModel.InvalidAsynchronousStateException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ComponentModel.InvalidEnumArgumentException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ComponentModel.LicenseException?displayProperty=nameWithType> （使用.NET Core 2.0.4 和更新版本中，從.NET Framework 到.NET Core 不支援序列化）
- <xref:System.ComponentModel.WarningException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ComponentModel.Win32Exception?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Configuration.ConfigurationErrorsException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Configuration.ConfigurationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Configuration.Provider.ProviderException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Configuration.SettingsPropertyIsReadOnlyException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Configuration.SettingsPropertyNotFoundException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Configuration.SettingsPropertyWrongTypeException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ContextMarshalException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DBNull?displayProperty=nameWithType> （適用於.NET Core 2.0.2 和更新版本）   
- <xref:System.Data.Common.DbException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.ConstraintException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.DBConcurrencyException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.DataException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.DataSet?displayProperty=nameWithType>
- <xref:System.Data.DataTable?displayProperty=nameWithType> （除非 RemotingFormat 設 SerializationFormat.Binary 在此情況下它可以只交換與.NET Core 2.1 和更新版本。）   
- <xref:System.Data.DeletedRowInaccessibleException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.DuplicateNameException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.EvaluateException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.InRowChangingEventException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.InvalidConstraintException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.InvalidExpressionException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.MissingPrimaryKeyException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.NoNullAllowedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.Odbc.OdbcException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.OperationAbortedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.PropertyCollection?displayProperty=nameWithType>   
- <xref:System.Data.ReadOnlyException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.RowNotInTableException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.SqlClient.SqlException?displayProperty=nameWithType> （使用.NET Core 2.0.4 和更新版本中，從.NET Framework 到.NET Core 不支援序列化）
- <xref:System.Data.SqlTypes.SqlAlreadyFilledException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.SqlTypes.SqlBoolean?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlByte?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDateTime?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlDouble?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlGuid?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt16?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt32?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlInt64?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlNotFilledException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.SqlTypes.SqlNullValueException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.SqlTypes.SqlString?displayProperty=nameWithType>   
- <xref:System.Data.SqlTypes.SqlTruncateException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.SqlTypes.SqlTypeException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.StrongTypingException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.SyntaxErrorException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Data.VersionNotFoundException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DataMisalignedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DateTime?displayProperty=nameWithType>   
- <xref:System.DateTimeOffset?displayProperty=nameWithType>   
- <xref:System.Decimal?displayProperty=nameWithType>   
- `System.Diagnostics.Contracts.ContractException` <!--zz <xref:System.Diagnostics.Contracts.ContractException?displayProperty=nameWithType> --> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Diagnostics.Tracing.EventSourceException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.IO.DirectoryNotFoundException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.AccountManagement.MultipleMatchesException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.AccountManagement.NoMatchingPrincipalException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.AccountManagement.PasswordException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.AccountManagement.PrincipalException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.AccountManagement.PrincipalExistsException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.AccountManagement.PrincipalOperationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.AccountManagement.PrincipalServerDownException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectExistsException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryObjectNotFoundException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryOperationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.ActiveDirectory.ActiveDirectoryServerDownException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.ActiveDirectory.ForestTrustCollisionException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.ActiveDirectory.SyncFromAllServersOperationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.DirectoryServicesCOMException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.Protocols.BerConversionException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.Protocols.DirectoryException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.Protocols.DirectoryOperationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.Protocols.LdapException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DirectoryServices.Protocols.TlsOperationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DivideByZeroException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.DllNotFoundException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Double?displayProperty=nameWithType>   
- <xref:System.Drawing.Color?displayProperty=nameWithType>   
- <xref:System.Drawing.Point?displayProperty=nameWithType>   
- <xref:System.Drawing.PointF?displayProperty=nameWithType>   
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>   
- <xref:System.Drawing.RectangleF?displayProperty=nameWithType>   
- <xref:System.Drawing.Size?displayProperty=nameWithType>   
- <xref:System.Drawing.SizeF?displayProperty=nameWithType>   
- <xref:System.DuplicateWaitObjectException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.EntryPointNotFoundException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Enum?displayProperty=nameWithType>   
- <xref:System.EventArgs?displayProperty=nameWithType> （適用於.NET Core 2.0.6 和更新版本）
- <xref:System.Exception?displayProperty=nameWithType>   
- <xref:System.ExecutionEngineException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.FieldAccessException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.FormatException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Globalization.CompareInfo?displayProperty=nameWithType>   
- <xref:System.Globalization.CultureNotFoundException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Globalization.SortVersion?displayProperty=nameWithType>   
- <xref:System.Guid?displayProperty=nameWithType>   
- `System.IO.Compression.ZLibException` <!--zz <xref:System.IO.Compression.ZLibException?displayProperty=nameWithType --> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.IO.DriveNotFoundException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.IO.EndOfStreamException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.IO.FileFormatException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.IO.FileLoadException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.IO.FileNotFoundException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.IO.IOException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.IO.InternalBufferOverflowException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.IO.InvalidDataException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.IO.IsolatedStorage.IsolatedStorageException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.IO.PathTooLongException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.InsufficientExecutionStackException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.InsufficientMemoryException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Int16?displayProperty=nameWithType>   
- <xref:System.Int32?displayProperty=nameWithType>   
- <xref:System.Int64?displayProperty=nameWithType>   
- <xref:System.IntPtr?displayProperty=nameWithType>   
- <xref:System.InvalidCastException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.InvalidOperationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.InvalidProgramException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.InvalidTimeZoneException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.MemberAccessException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.MethodAccessException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.MissingFieldException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.MissingMemberException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.MissingMethodException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.MulticastNotSupportedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Net.Cookie?displayProperty=nameWithType>   
- <xref:System.Net.CookieCollection?displayProperty=nameWithType>   
- <xref:System.Net.CookieContainer?displayProperty=nameWithType>   
- <xref:System.Net.CookieException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Net.HttpListenerException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Net.Mail.SmtpException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Net.Mail.SmtpFailedRecipientException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Net.Mail.SmtpFailedRecipientsException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Net.NetworkInformation.NetworkInformationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Net.NetworkInformation.PingException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Net.ProtocolViolationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Net.Sockets.SocketException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Net.WebException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Net.WebSockets.WebSocketException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.NotFiniteNumberException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.NotImplementedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.NotSupportedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.NullReferenceException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Nullable%601?displayProperty=nameWithType>   
- <xref:System.Numerics.BigInteger?displayProperty=nameWithType>   
- <xref:System.Numerics.Complex?displayProperty=nameWithType>   
- <xref:System.Object?displayProperty=nameWithType>   
- <xref:System.ObjectDisposedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.OperationCanceledException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.OutOfMemoryException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.OverflowException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.PlatformNotSupportedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.RankException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Reflection.AmbiguousMatchException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Reflection.CustomAttributeFormatException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Reflection.InvalidFilterCriteriaException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Reflection.ReflectionTypeLoadException?displayProperty=nameWithType> （使用.NET Core 2.0.4 和更新版本中，從.NET Framework 到.NET Core 不支援序列化）
- <xref:System.Reflection.TargetException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Reflection.TargetInvocationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Reflection.TargetParameterCountException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Resources.MissingManifestResourceException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Resources.MissingSatelliteAssemblyException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Runtime.CompilerServices.RuntimeWrappedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Runtime.InteropServices.COMException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Runtime.InteropServices.ExternalException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Runtime.InteropServices.InvalidComObjectException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Runtime.InteropServices.InvalidOleVariantTypeException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Runtime.InteropServices.MarshalDirectiveException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Runtime.InteropServices.SEHException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Runtime.Serialization.InvalidDataContractException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Runtime.Serialization.SerializationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.SByte?displayProperty=nameWithType>   
- <xref:System.Security.AccessControl.PrivilegeNotHeldException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Security.Authentication.AuthenticationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Security.Authentication.InvalidCredentialException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Security.Cryptography.CryptographicException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Security.Cryptography.CryptographicUnexpectedOperationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- `System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException` <!--zz <xref:System.Security.Cryptography.Xml.CryptoSignedXmlRecursionException?displayProperty=nameWithType --> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Security.HostProtectionException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Security.Policy.PolicyException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Security.Principal.IdentityNotMappedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Security.SecurityException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本中，受限制的序列化資料）
- <xref:System.Security.VerificationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Security.XmlSyntaxException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ServiceProcess.TimeoutException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Single?displayProperty=nameWithType>   
- <xref:System.StackOverflowException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.String?displayProperty=nameWithType>   
- <xref:System.StringComparer?displayProperty=nameWithType>   
- <xref:System.SystemException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Text.DecoderFallbackException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Text.EncoderFallbackException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Text.RegularExpressions.RegexMatchTimeoutException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Text.StringBuilder?displayProperty=nameWithType>   
- <xref:System.Threading.AbandonedMutexException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Threading.BarrierPostPhaseException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Threading.LockRecursionException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Threading.SemaphoreFullException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Threading.SynchronizationLockException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Threading.Tasks.TaskCanceledException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Threading.Tasks.TaskSchedulerException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Threading.ThreadAbortException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Threading.ThreadInterruptedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Threading.ThreadStartException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Threading.ThreadStateException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Threading.WaitHandleCannotBeOpenedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.TimeSpan?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo.AdjustmentRule?displayProperty=nameWithType>   
- <xref:System.TimeZoneInfo?displayProperty=nameWithType>   
- <xref:System.TimeZoneNotFoundException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.TimeoutException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Transactions.TransactionAbortedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Transactions.TransactionException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Transactions.TransactionInDoubtException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Transactions.TransactionManagerCommunicationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Transactions.TransactionPromotionException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Tuple?displayProperty=nameWithType>   
- <xref:System.TypeAccessException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.TypeInitializationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.TypeLoadException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.TypeUnloadedException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.UInt16?displayProperty=nameWithType>   
- <xref:System.UInt32?displayProperty=nameWithType>   
- <xref:System.UInt64?displayProperty=nameWithType>   
- <xref:System.UIntPtr?displayProperty=nameWithType>   
- <xref:System.UnauthorizedAccessException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Uri?displayProperty=nameWithType>   
- <xref:System.UriFormatException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.ValueTuple?displayProperty=nameWithType> （不在.NET Framework 4.7 及較早版本中序列化）  
- <xref:System.ValueType?displayProperty=nameWithType>   
- <xref:System.Version?displayProperty=nameWithType>   
- <xref:System.WeakReference%601?displayProperty=nameWithType>   
- <xref:System.WeakReference?displayProperty=nameWithType>   
- <xref:System.Xml.Schema.XmlSchemaException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Xml.Schema.XmlSchemaInferenceException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Xml.Schema.XmlSchemaValidationException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Xml.XPath.XPathException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Xml.XmlException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Xml.Xsl.XsltCompileException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）
- <xref:System.Xml.Xsl.XsltException?displayProperty=nameWithType> （適用於.NET Core 2.0.4 和更新版本）

## <a name="in-this-section"></a>本節內容

 [序列化概念](../../../docs/standard/serialization/serialization-concepts.md)  
 討論兩種使用序列化會很有用的案例：一是將資料持續至儲存區，一是跨應用程式定義域傳遞物件。  
  
 [基本序列化](../../../docs/standard/serialization/basic-serialization.md)  
 說明如何使用二進位與 SOAP 格式子來序列化物件。  
  
 [選擇式序列化](../../../docs/standard/serialization/selective-serialization.md)  
 說明如何避免序列化某些類別的成員。  
  
 [自訂序列化](../../../docs/standard/serialization/custom-serialization.md)  
 描述如何使用 <xref:System.Runtime.Serialization.ISerializable> 介面自訂類別的序列化。  
  
 [序列化程序中的步驟](../../../docs/standard/serialization/steps-in-the-serialization-process.md)  
 說明在格式子上呼叫 <xref:System.Runtime.Serialization.Formatter.Serialize%2A> 方法時，執行序列化工作的過程。  
  
 [版本相容序列化](../../../docs/standard/serialization/version-tolerant-serialization.md)  
 說明如何建立可隨時間變更序列化型別，而不會造成應用程式擲回例外狀況。  
  
 [序列化方針](../../../docs/standard/serialization/serialization-guidelines.md)  
 提供決定何時序列化物件的幾個基本指導原則。  
  
## <a name="reference"></a>參考資料  
 <xref:System.Runtime.Serialization>  
 包含類別，可以用來序列化和還原序列化物件。  
  
## <a name="related-sections"></a>相關章節  
 [XML 和 SOAP 序列化](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
 說明 Common Language Runtime 中所含的 XML 序列化機制。  
  
 [安全性和序列化](../../../docs/framework/misc/security-and-serialization.md)  
 說明在撰寫執行序列化的程式碼時要遵循的安全程式碼撰寫方針。  
  
 [遠端物件](https://msdn.microsoft.com/library/515686e6-0a8d-42f7-8188-73abede57c58)  
 說明 .NET Framework 中可用來進行遠端通訊的各種通訊方法。  
  
 [使用 ASP.NET 和 XML Web Service 用戶端建立的 XML Web Service](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c)  
 提供一個主題，說明並解釋如何設計使用 ASP.NET 建立的 XML Web 服務。
