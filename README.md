## NextJS API---> Aggregate & GroupBy

### Prisma aggregate() Method
![](https://imgur.com/cpc9gg2.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function GET(request: NextRequest) {
    try {
        
        const readData = await prisma.employee.aggregate({
            _count: {
                id: true,
            },
            _sum: {
                salary: true,
            },
            _avg: {
                salary: true,
            },
            _min: {
                salary: true,
            },
            _max: {
                salary: true,
            }
        });

        return NextResponse.json(
            {status: "success", message: "Read data successfully", data: readData},
            {status: 200}
        )
    } catch (error) {
        return NextResponse.json(
            {status: "failed", message: "Internal server problem"},
            {status: 500}
        )
    }
}
```
---

### Prisma groupBy() Method
![](https://imgur.com/GcmdD8E.png)

```bash
const readData = await prisma.employee.groupBy({
            by: ['city'],
        });
```
---

### Prisma groupBy() with Count
![](https://imgur.com/7s5lPny.png)

```bash
const readData = await prisma.employee.groupBy({
            by: ['city'],
            _count: {
                id: true,
            }
        });
```
---

### Prisma groupBy() with Sum
![](https://imgur.com/IWyKhHq.png)

```bash
const readData = await prisma.employee.groupBy({
            by: ['city'],
            _sum: {
                salary: true,
            }
        });
```
---

### Prisma groupBy() with Having Clause
![](https://imgur.com/wA3VEGo.png)

```bash
const readData = await prisma.employee.groupBy({
            by: ['city'],
            _sum: {
                salary: true,
            },
            having: {
                city: 'Dhaka'
            }
        });
```
---
