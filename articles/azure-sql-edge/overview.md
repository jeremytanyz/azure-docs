---
title: What is Azure SQL Edge? 
description: Learn about Azure SQL Edge
keywords: introduction to SQL Edge,what is SQL Edge, SQL Edge overview
services: sql-edge
ms.service: sql-edge
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: jroth
ms.date: 05/19/2020
---

# What is Azure SQL Edge?

Azure SQL Edge is an optimized relational database engine geared for IoT and IoT Edge deployments. It provides capabilities to create a high-performance data storage and processing layer for IoT applications and solutions. Azure SQL Edge provides capabilities to stream, process, and analyze relational and non-relational such as JSON, graph and time-series data, which makes it the right choice for a variety of modern IoT applications.

Azure SQL Edge is built on the latest versions of the [SQL Server Database Engine](/sql/sql-server/sql-server-technical-documentation), which provides industry-leading performance, security and query processing capabilities. Since Azure SQL Edge is built on the same engine as [SQL Server](/sql/sql-server/sql-server-technical-documentation) and [Azure SQL](/azure/azure-sql/index), it provides the same Transact-SQL (T-SQL) programming surface area that makes development of applications or solutions easier and faster, and makes application portability between IoT Edge devices, data centers and the cloud straight forward.

What is Azure SQL Edge video on Channel 9:
> [!VIDEO https://docs.microsoft.com/shows/Data-Exposed/What-is-Azure-SQL-Edge/player]

## Deployment Models

Azure SQL Edge supports two deployment modes.

- Connected deployment through Azure IoT Edge: Azure SQL Edge is available on the Azure Marketplace and can be deployed as a module for [Azure IoT Edge](../iot-edge/about-iot-edge.md). For more information, see [Deploy Azure SQL Edge](deploy-portal.md).<br>

![SQL Edge overview diagram](media/overview/overview.png)

- Disconnected deployment: Azure SQL Edge container images can be pulled from docker hub and deployed either as a standalone docker container or on a kubernetes cluster. For more information, see [Deploy Azure SQL Edge with Docker](disconnected-deployment.md) and [Deploy an Azure SQL Edge container in Kubernetes](deploy-kubernetes.md).

## Editions of SQL Edge

SQL Edge is available with two different editions or software plans. These editions have identical feature sets and only differ in terms of their usage rights and the amount of cpu/memory they support.

   |**Plan**  |**Description**  |
   |---------|---------|
   |Azure SQL Edge Developer  |  Development only sku, each SQL Edge container is limited to upto 4 cores and 32 GB Memory  |
   |Azure SQL Edge    |  Production sku,  each SQL Edge container is limited to upto 8 cores and 64 GB Memory. |

## Pricing and Availability

Azure SQL Edge is now generally available. For more information on the pricing and availability in specific regions, see [Azure SQL Edge](https://azure.microsoft.com/services/sql-edge/).

> [!IMPORTANT]
> To understand the feature differences between Azure SQL Edge and SQL Server, as well as the differences among different Azure SQL Edge options, see [Supported features of Azure SQL Edge](features.md).

## Streaming Capabilities  

Azure SQL Edge provides built in streaming capabilities for real-time analytics and complex event-processing. The streaming capability is built using the same constructs as [Azure Stream Analytics](../stream-analytics/stream-analytics-introduction.md) and  similar capabilities as [Azure Stream Analytics on IoT Edge](../stream-analytics/stream-analytics-edge.md).

The streaming engine for Azure SQL Edge is designed for low-latency, resiliency, efficient use of bandwidth and compliance. 

For more information on data streaming in SQL Edge, refer [Data Streaming](stream-data.md)

## Machine Learning and Artificial Intelligence Capabilities

Azure SQL Edge provides built-in machine learning and analytics capabilities by integrating the open format ONNX (Open Neural Network Exchange) runtime, which allows exchange of deep learning and neural network models between different frameworks. For more information on ONNX, see [here](https://onnx.ai/). ONNX runtime provides the flexibility to develop models in a language or tools of your choice, which can then be converted to the ONNX format for execution within SQL Edge. For more information, see [Machine Learning and Artificial Intelligence with ONNX in SQL Edge](onnx-overview.md).

## Working with Azure SQL Edge

Azure SQL Edge makes developing and maintaining applications easier and more productive. Users can use all the familiar tools and skills to build great apps and solutions for their IoT Edge needs. User can develop in SQL Edge using tools like the following:

- [The Azure portal](https://portal.azure.com/) - A web-based application for managing all Azure services.
- [SQL Server Management Studio](/sql/ssms/download-sql-server-management-studio-ssms/) - A free, downloadable client application for managing any SQL infrastructure, from SQL Server to SQL Database.
- [SQL Server Data Tools in Visual Studio](/sql/ssdt/download-sql-server-data-tools-ssdt/) - A free, downloadable client application for developing SQL Server relational databases, SQL databases, Integration Services packages, Analysis Services data models, and Reporting Services reports.
- [Azure Data Studio](/sql/azure-data-studio/what-is/) - A free, downloadable, cross platform database tool for data professional using the Microsoft family of on-premises and cloud data platforms on Windows, macOS, and Linux.
- [Visual Studio Code](https://code.visualstudio.com/docs) - A free, downloadable, open-source code editor for Windows, macOS, and Linux. It supports extensions, including the [mssql extension](https://aka.ms/mssql-marketplace) for querying Microsoft SQL Server, Azure SQL Database, and Azure Synapse Analytics.


## Next steps

- [Deploy SQL Edge through Azure portal](deploy-portal.md)
- [Machine Learning and Artificial Intelligence with SQL Edge](onnx-overview.md)
- [Building an end-to-end IoT solution with SQL Edge](tutorial-deploy-azure-resources.md)