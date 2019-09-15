---
title: 作法：將執行個體資料屬性還原序列化
ms.date: 03/30/2017
ms.assetid: b13a3508-1b97-4359-b336-03d85fa23bc4
ms.openlocfilehash: e037d5f8d0b221aa0eb8fdc6eceabf6efb2dc387
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989627"
---
# <a name="how-to-deserialize-instance-data-properties"></a>HOW TO：將執行個體資料屬性還原序列化
有時候，使用者或工作流程管理員可能會想要手動檢查持續工作流程執行個體的狀態。 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 提供公開下列四個資料行的執行個體資料表檢視：  
  
- ReadWritePrimitiveDataProperties  
  
- WriteOnlyPrimitiveDataProperties  
  
- ReadWriteComplexDataProperties  
  
- WriteOnlyComplexDataProperties  
  
 基本資料屬性會參考其 .NET Framework 類型視為「通用」（例如，Int32 和 String）的屬性，而複雜的資料屬性則是指所有其他類型。 稍後在這個程式碼範例中可找到完整的基本類型列舉。  
  
 讀/寫屬性是指在執行個體載入時傳回至工作流程執行階段的屬性。 WriteOnly 屬性寫入至資料庫，絕不再次讀取。  
  
 這個範例提供可讓使用者還原序列化基本資料屬性的程式碼。 指定從 ReadWritePrimitiveDataProperties 或 WriteOnlyPrimitiveDataProperties 資料行讀取的位元組陣列時，此程式碼會將二進位大型物件（BLOB）轉換成<xref:System.Collections.Generic.Dictionary%602>類型\<XName，物件 >，其中每個索引鍵值配對代表屬性名稱及其對應的值。  
  
 這個範例不示範如何還原序列化複雜資料屬性，因為目前不支援此作業。  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.IO;  
using System.IO.Compression;  
using System.Xml.Linq;  
using System.Xml;  
using System.Globalization;  
using System.Data.SqlClient;  
  
namespace PropertyReader  
{  
    class Program  
    {  
        const string ConnectionString = @"Data Source=localhost;Initial Catalog=Persistence;Integrated Security=True;Asynchronous Processing=True";  
        static void Main(string[] args)  
        {  
            string queryString = "SELECT TOP 10 * FROM [System.Activities.DurableInstancing].[Instances]";  
  
            using (SqlConnection connection =  
                       new SqlConnection(ConnectionString))  
            {  
                SqlCommand command =  
                    new SqlCommand(queryString, connection);  
                connection.Open();  
  
                SqlDataReader reader = command.ExecuteReader();  
  
                byte encodingOption;  
  
                while (reader.Read())  
                {  
                    if (reader["ReadWritePrimitiveDataProperties"] != DBNull.Value)  
                    {  
                        encodingOption = (byte)reader["EncodingOption"];  
                        Console.WriteLine("Printing the ReadWritePrimitiveDataProperties of the instance with Id:" + reader["InstanceId"]);  
                        foreach (KeyValuePair<XName, object> pair in (Dictionary<XName, object>)ReadDataProperties((byte[])reader["ReadWritePrimitiveDataProperties"], encodingOption))  
                        {  
                            Console.WriteLine("{0}, {1}" , pair.Key, pair.Value);  
                        }  
                        Console.WriteLine();  
                    }  
                    if (reader["WriteOnlyPrimitiveDataProperties"] != DBNull.Value)  
                    {  
                        encodingOption = (byte)reader["EncodingOption"];  
                        Console.WriteLine("Printing the WriteOnlyPrimitiveDataProperties of the instance with Id:" + reader["InstanceId"]);  
                        foreach (KeyValuePair<XName, object> pair in (Dictionary<XName, object>)ReadDataProperties((byte[])reader["WriteOnlyPrimitiveDataProperties"], encodingOption))  
                        {  
                            Console.WriteLine("{0}, {1}", pair.Key, pair.Value);  
                        }  
                        Console.WriteLine();  
                    }  
                }  
  
                // Call Close when done reading.  
                reader.Close();  
            }  
  
            Console.ReadLine();  
  
        }  
  
        static Dictionary<XName, object> ReadDataProperties(byte[] serializedDataProperties, byte encodingOption)  
        {  
            if (serializedDataProperties != null)  
            {  
                Dictionary<XName, object> propertyBag = new Dictionary<XName, object>();  
                bool isCompressed = (encodingOption == 1);  
  
                using (MemoryStream memoryStream = new MemoryStream(serializedDataProperties))  
                {  
                    // if the instance state is compressed using GZip algorithm  
                    if (isCompressed)  
                    {  
                        // decompress the data using the GZip   
                        using (GZipStream stream = new GZipStream(memoryStream, CompressionMode.Decompress))  
                        {  
                            // create an XmlReader object and pass it on to the helper method ReadPrimitiveDataProperties  
                            using (XmlReader reader = XmlDictionaryReader.CreateBinaryReader(stream, XmlDictionaryReaderQuotas.Max))  
                            {  
                                // invoke the helper method  
                                ReadPrimitiveDataProperties(reader, propertyBag);  
                            }  
                        }  
                    }  
                    else  
                    {  
                        // if the instance data is not compressed   
                        // create an XmlReader object and pass it on to the helper method ReadPrimitiveDataProperties  
                        using (XmlReader reader = XmlDictionaryReader.CreateBinaryReader(memoryStream, XmlDictionaryReaderQuotas.Max))  
                        {  
                            // invoke the helper method  
                            ReadPrimitiveDataProperties(reader, propertyBag);  
                        }  
                    }  
                    return propertyBag;  
                }  
            }  
  
            return null;  
        }  
  
        // reads the primitive data properties from the XML stream  
        // invoked by the ReadDataProperties method  
        static void ReadPrimitiveDataProperties(XmlReader reader, Dictionary<XName, object> propertyBag)  
        {  
            const string xmlElementName = "Property";  
  
            if (reader.ReadToDescendant(xmlElementName))  
            {  
                do  
                {  
                    // get the name of the property  
                    reader.MoveToFirstAttribute();  
                    string propertyName = reader.Value;  
  
                    // get the type of the property  
                    reader.MoveToNextAttribute();  
                    PrimitiveType type = (PrimitiveType)Int32.Parse(reader.Value, CultureInfo.InvariantCulture);  
  
                    // get the value of the property  
                    reader.MoveToNextAttribute();  
                    object propertyValue = ConvertStringToNativeType(reader.Value, type);  
  
                    // add the name and value of the property to the property bag  
                    propertyBag.Add(propertyName, propertyValue);  
                }  
  
                while (reader.ReadToNextSibling(xmlElementName));  
            }  
        }  
  
        // invoked by the ReadPrimitiveDataProperties method  
        // Given a property value as parsed from an XML attribute, and the .NET Type of the Property, recreates the actual property value  
        // (e.g. Given a property value of "1" and a PrimitiveType of Int32, this method will return an object of type Int32 with value 1)  
        static object ConvertStringToNativeType(string value, PrimitiveType type)  
        {  
            switch (type)  
            {  
                case PrimitiveType.Bool:  
                    return XmlConvert.ToBoolean(value);  
                case PrimitiveType.Byte:  
                    return XmlConvert.ToByte(value);  
                case PrimitiveType.Char:  
                    return XmlConvert.ToChar(value);  
                case PrimitiveType.DateTime:  
                    return XmlConvert.ToDateTime(value, XmlDateTimeSerializationMode.RoundtripKind);  
                case PrimitiveType.DateTimeOffset:  
                    return XmlConvert.ToDateTimeOffset(value);  
                case PrimitiveType.Decimal:  
                    return XmlConvert.ToDecimal(value);  
                case PrimitiveType.Double:  
                    return XmlConvert.ToDouble(value);  
                case PrimitiveType.Float:  
                    return float.Parse(value, CultureInfo.InvariantCulture);  
                case PrimitiveType.Guid:  
                    return XmlConvert.ToGuid(value);  
                case PrimitiveType.Int:  
                    return XmlConvert.ToInt32(value);  
                case PrimitiveType.Long:  
                    return XmlConvert.ToInt64(value);  
                case PrimitiveType.SByte:  
                    return XmlConvert.ToSByte(value);  
                case PrimitiveType.Short:  
                    return XmlConvert.ToInt16(value);  
                case PrimitiveType.String:  
                    return value;  
                case PrimitiveType.TimeSpan:  
                    return XmlConvert.ToTimeSpan(value);  
                case PrimitiveType.Type:  
                    return Type.GetType(value);  
                case PrimitiveType.UInt:  
                    return XmlConvert.ToUInt32(value);  
                case PrimitiveType.ULong:  
                    return XmlConvert.ToUInt64(value);  
                case PrimitiveType.Uri:  
                    return new Uri(value);  
                case PrimitiveType.UShort:  
                    return XmlConvert.ToUInt16(value);  
                case PrimitiveType.XmlQualifiedName:  
                    return new XmlQualifiedName(value);  
                case PrimitiveType.Null:  
                case PrimitiveType.Unavailable:  
                default:  
                    return null;  
            }  
        }  
        // .NET Types which SQL Workflow Instance Store considers to be Primitive. Any other .NET type not listed in this enumeration is a "Complex" property.  
        enum PrimitiveType  
        {  
            Bool = 0,  
            Byte,  
            Char,  
            DateTime,  
            DateTimeOffset,  
            Decimal,  
            Double,  
            Float,  
            Guid,  
            Int,  
            Null,  
            Long,  
            SByte,  
            Short,  
            String,  
            TimeSpan,  
            Type,  
            UInt,  
            ULong,  
            Uri,  
            UShort,  
            XmlQualifiedName,  
            Unavailable = 99  
        }  
    }  
}  
```
