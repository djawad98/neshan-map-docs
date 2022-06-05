
# نقشه «نشان» همراه با فیچرهای اختصاصی

  

<div  dir="rtl">

یک پکیج برای کار با نقشه «نشان» همراه با فیچر/ویژگی های اختصاصی

  
  

این پکیج از فایل های جی اس و سی اس اس ارائه شده توسط نشان استفاده میکند. این فایلها در واقع یک `wrapper` برای کتابخانه معروف [`leaflet`](https://leafletjs.com) می باشد. لذا مطالعه [مستندات](https://leafletjs.com/reference.html) مربوط به کتابخانه `leaflet` ضروری است.

  

- [صفحه leaflet در نشان](https://platform.neshan.org/sdk/web-sdk-getting-started)

- [مستندات کتابخانه leaflet](https://leafletjs.com/reference.html)

  
  
  

## لیست فیچر/ماژول ها

- 🖋️ Polygon ( رسم چند ضلعی )

- 🔎 Search ( جستجو )

- 📌 Pin ( قراردادن پین )

- 🗺️ Locate ( موقعیت یابی )

- 🌏 Geocoding ( تبدیل مختصات به آدرس متنی )

- 📍 CenteralPin ( قراردادن پین به سبک اسنپ )

  
  
  

<br>

<br>

<br>

  

# نحوه استفاده

  

1. با دستور زیر پکیج را از `npm` نصب کنید

<div  dir="ltr">

  

npm i @djawad98/frotel-map -S

  

</div>

  

این پکیج دو نوع خروجی `esmodule` و `umd` را در اختیار شما قرار میدهد. لذا باید از یک باندلر مثل `webpack` یا `vite` یا ... استفاده کنید.

  

<br>

<br>

  

2. تگ اسکریپت زیر را در `<head>` داکیومنت خود اضافه کنید

  

<script  src="https://static.neshan.org/sdk/leaflet/1.4.0/leaflet.js"></script>

  
  
  

3. سپس فراخوانی کنید

<div  dir="ltr">

  
  

import { Map } from "@djawad98/frotel-map";

  
  

const mapp = new Map('map_id', {

key: 'xxxx',

serviceKey: 'zzzz'

})

</div>

  

حالا امکان مشاهده نقشه را خواهید داشت.

توجه داشته باشید که باید کلیدهای مربوط به نمایش نقشه `web key` و دسترسی به سرویس `service key` را از پنل خود در نشان بدست بیاورید و در فیلدهای بالا قرار دهید.

  

<br>

<br>

  

<div  dir="ltr">

  
  

const mapp = new Map( el, ?options{} )

  

</div>

  

`el` : آیدی عنصر مورد نظر که نقشه در داخل آن نمایش داده میشود (بدون علامت # ابتدایی)

  

`options`: آبجکتی شامل آپشن های نقشه

  

<br>

<br>

<br>

  

# متد add

با استفاده از متد `add` روی اینستنس اصلی نقشه میتوانید این ماژول را اضافه کنید. این متد در جواب، اینستنس مربوط به ماژول `Polygon` برمیگرداند.

<div  dir="ltr">

  

mapInstance.add( moduleName, moduleOptions)

  

</div>

<hr>

<br>

  

## آپشن های نقشه

  
  

## `key`

`type: string`

<br>

  

`default: null`

  

کلید مربوط به نمایش نقشه. (از طریق پنل کاربری خود در نشان بدست بیاورید.)

<br>

<br>

<hr>

  
  

<br>

  

## `servicekey`

`type: string`

<br>

  

`default: null`

  

کلید مربوط به استفاده از سرویس های نشان. به عنوان مثال سرویس جستجو یا تبدیل متخصات به آدرس متنی. (از طریق پنل کاربری خود در نشان بدست بیاورید.)

<br>

<br>

<hr>

  

<br>

  

## `readonly`

`type: boolean`

<br>

  

`default: false`

  

همه اینترکشن ها و فیچرهای مپ غیرفعال میشوند.به جز امکان زوم. فعال کردن این آپشن روی ماژول ها تاثیر میگذارد.

<br>

<br>

<hr>

  
  

<br>

  

## `center`

`type: array|object`

<br>

  

`default: [35.699739, 51.338097] | { lat: 35.699739, lng: 51.338097 }`

  

مختصات نمای نقشه هنگام لود اولیه.

<br>

<br>

<hr>

  

<br>

  

## `zoom`

`type: number`

<br>

  

`default: 12`

  

میزان بزرگنمایی نقشه هنگام لود اولیه

<br>

<br>

<hr>

  

<br>

  

## `leaflet`

`type: object`

<br>

  

`default: {}`

  

اگر مایلید مستقیما آپشنی را به هسته اصلی `leaflet` پاس بدهید از این طریق اقدام کنید. تمام آپشن هایی که در [مستندات `leaflet`](https://leafletjs.com/reference.html) آورده شده اند معتبر است.

<br>

<br>

<hr>

  
  

<br>

  

## `onReady`

`type: function`

<br>

  

`default: () => {}`

  

یک تابع تعریف کنید تا هنگامی که مپ به صورت کامل لود شد اجرا شود.

<br>

<br>

<br>

<br>

  
  
  

# 🖋️ Polygon

  

1. ماژول `Polygon` را از پکیج فراخوانی کنید.

<div  dir="ltr">

  
  

import { Map, Polygon } from "@djawad98/frotel-map";

  

const mapInstance = new Map('map_id', {

key: 'xxxx',

serviceKey: 'zzzz'

})

  

</div>

  

2. به هسته نقشه اضافه اش کنید

  

<div  dir="ltr">

  

const polygonInstance = mapInstance.add(Polygon, { options });

</div>

  
  

3. متد مورد نظر را فراخوانی کنید

<div  dir="ltr">

  

polygonInstance.drawPolygon( [ [1.324,2.32423], [4.324,2.32423],... ] )

</div>

  

# 🖋️ آپشن های Polygon

  
  
  

<br>

  

## `canSelectArea`

`type: boolean`

<br>

  

`default: false`

  

برای نمایش دکمه رسم چند ضلعی در پائین سمت راست نقشه

<br>

<br>

<hr>

<br>

  
  

<br>

  

## `drawMode`

`type: boolean`

<br>

  

`default: false`

  

برای فعال کردن دکمه رسم پالیگان به صورت پیشفرض هنگام لود نقشه

<br>

<br>

<hr>

<br>

  
  

<br>

  

## `preventIntersection`

`type: boolean`

<br>

  

`default: false`

  

برای فعال کردن حالت همپوشانی چند ضلعی جاری با چند ضلعی های موجود

<br>

<br>

<hr>

<br>

  
  

<br>

  

## `editableAfterShapeClosed`

`type: boolean`

<br>

  

`default: false`

  

با فعال کردن این ویژگی، بعد از رسم چندضلعی و بستن شکل، قابلیت ادیت چند ضلعی فراهم میشود.

<br>

<br>

<hr>

<br>

  
  

<br>

  

## `onShapeClosed`

`type: function`

<br>

  

`default: (coords) => {}`

  

تابعی به این آپشن پاس دهید تا هنگام بسته شدن شکل فراخوانی شود. این تابع در آرگومان اول مختصات چند ضلعی رسم شده را بر میگرداند. مطابق زیر:

<div  dir="ltr">

  
  

const polygonInstance = mapInstance.add(Polygon, {

  

onShapeClosed: coords => {

console.log(coord)

}

  

});

  
  

</div>

<br>

<br>

<hr>

<br>

  
  
  

<br>

  

## `onDrawing`

`type: function`

<br>

  

`default: (coords) => {}`

  

تابعی پاس دهید تا هنگام رسم چندضلعی به صورت پشت سرهم فراخوانی شود. به عنوان آرگومان اول، مختصات شکل در حال رسم را برمیگرداند.

  
  
  

<br>

<br>

<hr>

<br>

  
  
  

<br>

  

## `onEditedPolygon`

`type: function`

<br>

  

`default: (coords) => {}`

  

تابعی پاس دهید تا هنگام ویرایش چندضلعی فراخوانی شود. به عنوان آرگومان اول، مختصات شکل در حال ویرایش را برمیگرداند.

  
  
  

<br>

<br>

  
  

# 🖋️ متدهای Polygon

  

- **getCoordinates**

<div  dir="ltr">

  

polygonInstance.getCoordinates()

  
  

**returns** مختصات پالیگان حال حاضر (چه در حالت رسم چه در حالت بسته بودن )

  

`[[lat, lng], [lat, lng], ...]`

  

**parameters** *no parameters*

  

</div>

  

<br>

<br>

<hr>

<br>

  

- **drawPolygon**

برای رسم چندضلعی با مختصات داده شده. مطابق زیر

<div  dir="ltr">

  

polygonInstance.drawPolygon( [ [lat, lng], [lat, lng], [lat, lng], ... ] , "blue")

  

**parameters**

  

- `coords`: مختصات پالیگان مورد نظر

  

- `color`: رنگ پالیگان موردنظر

  

</div>

  

<br>

<br>

  
  
  

<br>

<br>

  

- **drawEditablePolygon**

برای رسم چندضلعی قابل *ویرایش* با مختصات داده شده. مطابق زیر

<div  dir="ltr">

  

polygonInstance.drawEditablePolygon( [ [lat, lng], [lat, lng], [lat, lng], ... ] , "blue")

  

**parameters**

  

- `coords`: مختصات پالیگان مورد نظر

  

- `color`: رنگ پالیگان موردنظر

  

</div>

  

<br>

<br>

<br>

  

# 🔎 Search

  

1. ماژول `Search` را از پکیج فراخوانی کنید

<div  dir="ltr">

  
  

import { Map, Search } from "@djawad98/frotel-map";

  

const mapInstance = new Map('map', {

key: 'xxxx',

...

})

  

</div>

2. به هسته نقشه اضافه اش کنید

<div  dir="ltr">

  

const searchInstance = mapInstance.add(Search, { options });

  

</div>

  

# 🔎 آپشن های Search

  
  
  

<br>

  

## `noPin`

`type: boolean`

<br>

  

`default: false`

  

برای فعال یا غیرفعال کردن قراردادن پین هنگام انتخاب یک موقعیت از لیست نتایج جستجو

  
  
  

<br>

<br>

  

# 📌 Pin

  

1. ماژول `Pin` را از پکیج فراخوانی کنید.

<div  dir="ltr">

  
  

import { Map, Pin } from "@djawad98/frotel-map";

  

const mapInstance = new Map('map', {

key: 'xxxx',

...

})

  

</div>

2. سپس به هسته اصلی مپ اضافه اش کنید

<div  dir="ltr">

  
  

const pinInstance = mapInstance.add(Pin, { options });

  

</div>

  

# 📌 آپشن های Pin

  
  
  
  

<br>

  

## `editMode`

`type: boolean`

<br>

  

`default: false`

  

با فعال کردن این آپشن امکان قرار دادن پین جدید از طریق دکمه مربوط به پین در پائین در سمت راست وجود نخواهد داشت.

  
  
  

<br>

<br>

<hr>

<br>

  

<br>

  

## `initialLatLng`

`type: array | object`

<br>

  

`default: null`

  

مختصات نمای ابتدایی نقشه که هنگام لود ابتدایی روی آن فوکوس میکند. مشابه کاری که متد [`setView`](https://leafletjs.com/reference.html#map-setview) در `leaflet` انجام میدهد.

  

*این آپشن به هسته اصلی نقشه منتقل خواهد شد*

  
  

<br>

<br>

<hr>

<br>

  

<br>

  

## `renderButton`

`type: boolean`

<br>

  

`default: true`

  

تعیین می کند که آیا دکمه قراردادن پین در پائین سمت راست نقشه نمایش داده شود یا خیر.

  

<br>

<br>

<hr>

<br>

  

<br>

  

## `centerMode`

`type: boolean`

<br>

  

`default: false`

  
  

این آپشن دکمه افزودن پین را غیر فعال میکند و امکان استفاده از ماژول `CentralPin` را فراهم میکند.

فعال کردن این آپشن هنگام استفاده از ماژول `CentralPin` ضروری است.

  
  

<br>

<br>

<hr>

<br>

  
  

<br>

  

## `maxPinCount`

`type: number`

<br>

  

`default: 1000`

  
  

حداکثر تعداد پین هایی که کاربر می تواند از طریق دکمه قرارداده شده در پائین سمت راست نقشه اضافه کند را مشخص میکند.

توجه داشته باشید که تعداد پین هایی که میتوان از طریق متد `addPin` اضافه کرد نامحدود هستند و این آپشن محدودیتی برای اضافه کردن پین از طریق این متد اعمال نمیکند.

  

<br>

<br>

<hr>

<br>

  
  
  

<br>

  

## `onPin`

`type: function`

<br>

  

`default: (coords) => {}`

  
  

تابعی پاس بدهید تا هنگام قرار دادن پین روی نقشه توسط کاربر، فراخوانی شود. به عنوان آرگومان اول مختصات نقظه ای که پین قرارداده شده را برمیگرداند.

  
  

<br>

<br>

  
  

# 📌 متدهای Pin

- **addPin**: یک پین یا مارکر جدید در مختصات داده شده قرار میدهد.

<div  dir="ltr">

  
  

pinInstance.addPin([lat, lng])

</div>

<br>

<br>

  

# 🗺️ Locate

  

این ماژول برای یافتن موقعیت کنونی کاربر استفاده میشود. توجه داشته باشید برای اینکه این ماژول به درستی کار کند نیاز به سرور امن `https` است. اگر روی لوکال تست می کنید حتما از مرورگر `edge` یا `firefox` استفاده کنید.

  

1. ماژول `Locate` را از پکیج فراخوانی کنید.

<div  dir="ltr">

  

import { Map, Locate } from "@djawad98/frotel-map";

  

const mapInstance = new Map('map', {

key: 'xxxx',

...

})

  

</div>

2. آنرا به هسته اصلی نقشه اضافه کنید.

<div  dir="ltr">

  
  

const locateInstance = mapInstance.add(Locate, { options });

  

</div>

  

# 🗺️ آپشن های Locate

  
  

<br>

<br>

  

## `noPin`

`type: boolean`

<br>

  

`default: false`

  

معین میکند که آیا موقع یافتن موقعیت کنونی کاربر در آن نقطه پین یا مارکر جدید قرار بدهد یا خیر

  

<br>

<br>

  
  

# 🗺️ متدهای Locate

- **findmyplace**: موقعیت کنونی کاربر را بر روی نقشه پیدا میکند و فوکوس نقشه را به آن موقعیت میبرد.

<div  dir="ltr">

  

pin.findmyplace()

</div>

  

<br>

<br>

<hr>

<br>

  

# 🌏 Geocoding

  

برای تبدیل مختصات به آدرس متنی استفاده میشود. نا صحیح این فیچر `reverse geocoding` است.

  

1. ماژول `Geocoding` را از پکیج فراخوانی کنید.

<div  dir="ltr">

  
  

import { Map, Geocoding } from "@djawad98/frotel-map";

  

const mapInstance = new Map('map', {

key: 'xxxx',

...

})

  

</div>

2. به هسته اصلی مپ اضافه اش کنید

<div  dir="ltr">

  
  

const geocodingInstance = mapInstance.add(Geocoding, { options });

  

</div>

  
  
  

<br>

<br>

  

# 🌏 متدهای Geocoding

  

- **getAddress**

آدرس متنی مختصات داده شده را برمیگرداند.

<div  dir="ltr">

  
  

geocodingInstance.getAddress( [ lat, lng ] )

  

**parameters**

  

- `latlng`: مختصات نقطه مورد نظر

  
  

**returns** آبجکتی حاوی اطلاعات آدرس نقطه مورد نظر، با ساختار زیر

  

</div>

  
  

توجه: این متد یک متد `async` است. مطابق زیر استفاده کنید.

<div  dir="ltr">

  
  

await geocodingInstance.getAddress([lat, lng])

  
  
  

// result object

{

"status": "OK",

"formatted_address": "تهران، دکتر فاطمی، حجاب، سازمان آب، بین دائمی و عبداله زاده",

"route_name": "سازمان آب",

"route_type": "secondary",

"neighbourhood": "فاطمي",

"city": "تهران",

"state": "استان تهران",

"place": null,

"municipality_zone": "6",

"in_traffic_zone": "true",

"in_odd_even_zone": "true",

"village": null,

"district": "بخش مرکزی شهرستان تهران",

}

  

</div>

  

*با توجه به نقطه انتخابی ممکن است تعدادی از فیلدها ارائه نشوند.*

[اطلاعات بیشتر](https://platform.neshan.org/api/reverse-geocoding)

  

<br>

<br>

<hr>

<br>

  
  
  

# 📍 CenteralPin

برای انتخاب نقطه ای روی نقشه به سبک انتخاب مبدا و مقصد در اسنپ

  
  
  

<br>

  

## `enableAddress`

`type: boolean`

<br>

  

`default: true`

  

معین میکند آیا بعد از قرارگرفتن پین روی نقشه آدرس متنی آن نقطه محاسبه شود یا خیر. با استفاده از آپشن `onFoundAddress` به نتیجه محاسبه دسترسی خواهید داشت.

  
  
  

<br>

<br>

<hr>

<br>

  
  
  

<br>

  

## `enablePopup`

`type: boolean`

<br>

  

`default: true`

  

معین میکند آیا پاپ آپ مربوط به آدرس نقطه روی پین نمایش داده شود یا خیر

  
  
  

<br>

<br>

<hr>

<br>

  

<br>

  

## `onPinUp`

`type: function`

<br>

  

`default: (latlng) => {}`

  

تابعی پاس بدهید تا هنگامی که پین از روی مپ برداشته/بلند میشود فراخوانی شود. به عنوان آرگومان اول محتضات نقطه را برمیگرداند.

  
  
  

<br>

<br>

<hr>

<br>

  
  

<br>

  

## `onPinDown`

`type: function`

<br>

  

`default: (latlng) => {}`

  

تابعی پاس بدهید تا هنگامی که پین روی مپ قرار میگیرد فراخوانی شود. به عنوان آرگومان اول محتضات نقطه را برمیگرداند.

  
  
  

<br>

<br>

<hr>

<br>

  
  
  

<br>

  

## `onFoundAddress`

`type: function`

<br>

  

`default: (address) => {}`

  

اگر آپشن `enableAddress` فعال باشد، هنگامی که پین روی مپ مینشیند این تابع با کمی تاخیر فراخوانی میشود. به عنوان آرگومان اول اطلاعات آدرسی نقطه ر برمیگرداند.

  
  

<br>

<br>

<hr>

<br>

  
  
  
  
  

<br>

<br>

<br>

  

<div  dir="ltr">

  

# UX Shortcuts

- `Undo polygon point`: to undo the last point, right-click anywhere on the map.

  

- `Closing the shape`: to close the shape when drawing, just double click to close the shape automatically.

  

- `Cancel pin`: to discard current pin, right click on the map

  

# Author and Maintainer

This package is written with Vanilla JavaScript by **Javad Ghased** for Frotel.com.

  

- [Github](https://github.com/djawad98)

- [Email](mailto:ghasedjavad@gmail.com)

</div>

</div>
