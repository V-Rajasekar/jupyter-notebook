## Converting Date and Time to String format


```Java
import java.text.DateFormat;

import java.text.SimpleDateFormat;

import java.time.LocalDateTime;

import java.time.LocalDate;

import java.time.format.DateTimeFormatter;

import java.util.Calendar;

import java.util.Date;


private static final DateFormat sdf = new SimpleDateFormat("yyyy/MM/dd HH:mm:ss");

private static final DateTimeFormatter dtf = DateTimeFormatter.ofPattern("yyyy/MM/dd HH:mm:ss");
//Java old libraries java.util.Date another api for formating java.text.SimpleDateFormat
        Date date = new Date();
        System.out.println(sdf.format(date));

        Calendar cal = Calendar.getInstance();
        System.out.println(sdf.format(cal.getTime()));

        LocalDateTime now = LocalDateTime.now();
        System.out.println(dtf.format(now));

        LocalDate localDate = LocalDate.now();
        System.out.println(DateTimeFormatter.ofPattern("yyy/MM/dd").format(localDate));


```

    2018/12/11 22:35:50
    2018/12/11 22:35:50
    2018/12/11 22:35:50
    2018/12/11
    

## Converting String to local date Time


```Java
import java.text.DateFormat;

import java.text.SimpleDateFormat;

import java.time.LocalDateTime;

import java.time.LocalDate;

import java.time.format.DateTimeFormatter;

import java.util.Calendar;

import java.util.Date;

String now = "2017-06-13 12:30";
DateTimeFormatter formatter = DateTimeFormatter.ofPattern("yyyy-MM-dd HH:mm");

LocalDateTime formatDateTime = LocalDateTime.parse(now, formatter);
System.out.println("Before : " + now);

System.out.println("After : " + formatDateTime);
System.out.println("After : " + formatDateTime.format(formatter));

```

    Before : 2017-06-13 12:30
    After : 2017-06-13T12:30
    After : 2017-06-13 12:30
    

## Convert instant to localDateTime

Instant method return machine readable date times see(z) at the end


```Java
import java.time.LocalDateTime;

import java.time.LocalDate;

import java.time.ZoneOffset;

import java.time.Instant;

import java.time.format.DateTimeFormatter;

Instant instant = Instant.now();
System.out.println("Instant : " + instant);

LocalDateTime ldt = LocalDateTime.ofInstant(instant, ZoneOffset.UTC);
System.out.println("LocalDateTime : " + ldt);

```

    Instant : 2018-12-11T21:44:47.310717Z
    LocalDateTime : 2018-12-11T21:44:47.310717
    


## Convert Date to LocalDate and LocalDateTime


```Java
import java.time.*;
import java.time.chrono.Chronology;
import java.time.chrono.ChronoLocalDate;
import java.util.Date;
import java.time.temporal.TemporalAdjusters;

ZoneId defaultZoneId = ZoneId.systemDefault();
System.out.println("System Default TimeZone : " + defaultZoneId);

Date date = new Date();
System.out.println("date : " + date);

Instant instant = date.toInstant();
System.out.println("instant : " + instant); 

//2. Instant + system default time zone + toLocalDate() = LocalDate

LocalDate localDate = instant.atZone(defaultZoneId).toLocalDate();

System.out.println("localDate : " + localDate);

//3. Instant + system default time zone + toLocalDateTime() = LocalDateTime

LocalDateTime localDateTime = instant.atZone(defaultZoneId).toLocalDateTime();

System.out.println("localDateTime : " + localDateTime);



//4. Instant + system default time zone = ZonedDateTime

ZonedDateTime zonedDateTime = instant.atZone(defaultZoneId);

System.out.println("zonedDateTime : " + zonedDateTime);

//In Java 8, predefined java.time.temporal.TemporalAdjusters can be used to adjust a date or Temporal.

//Please read below example to print last day of current month and next monday date.
LocalDate with1 = localDate.with(TemporalAdjusters.lastDayOfMonth());
System.out.println("lastDayOfMonth : " + with1);

LocalDate with2 = localDate.with(TemporalAdjusters.next(DayOfWeek.MONDAY));
System.out.println("next monday : " + with2);


Set<Chronology> chronos = Chronology.getAvailableChronologies();

       for (Chronology chrono : chronos) {

           ChronoLocalDate date = chrono.dateNow();

           System.out.printf("   %20s: %s%n", chrono.getId(), date.toString());

       }

```

    System Default TimeZone : Europe/Berlin
    date : Tue Dec 11 22:55:51 CET 2018
    instant : 2018-12-11T21:55:51.940Z
    localDate : 2018-12-11
    localDateTime : 2018-12-11T22:55:51.940
    zonedDateTime : 2018-12-11T22:55:51.940+01:00[Europe/Berlin]
    lastDayOfMonth : 2018-12-31
    next monday : 2018-12-17
                     Minguo: Minguo ROC 107-12-11
                   Japanese: Japanese Heisei 30-12-11
               ThaiBuddhist: ThaiBuddhist BE 2561-12-11
                        ISO: 2018-12-11
            Hijrah-umalqura: Hijrah-umalqura AH 1440-04-04
    


```Java

```
