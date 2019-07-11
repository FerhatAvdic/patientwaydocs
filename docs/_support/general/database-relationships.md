---
layout: section-page
title:  "Database Relationshops"
section: 02-02-01
tags: general
---

## PatientWay Application Table Relationships

```plantuml
@startuml
' uncomment the line below if you're using computer with a retina display
' skinparam dpi 300
!define Table(name,desc) class name as "desc" << (T,#FFAAAA) >>
' we use bold for primary key
' green color for unique
' and underscore for not_null
!define primary_key(x) <b>x</b>
!define unique(x) <color:green>x</color>
!define not_null(x) <u>x</u>
' other tags available:
' <i></i>
' <back:COLOR></color>, where color is a color name or html color code
' (#FFAACC)
' see: http://plantuml.com/classes.html#More
hide methods
hide stereotypes

' entities

Table(encounters, "encounters\n(A kiosk use session)") {
primary_key(id) INTEGER
}

Table(encounter_values, "encounter_values\n(Values set during a session)") {
primary_key(id) INTEGER
not_null(encounter_id INTEGER
}

Table(call_queues, "call_queues") {
primary_key(id) INTEGER
}

Table(call_queue_histories, "call_queue_histories") {
primary_key(id) INTEGER
not_null(call_queue_id) INTEGER
}

Table(call_areas, "call_areas") {
primary_key(id) INTEGER
}

Table(versions, "versions") {
primary_key(id) INTEGER
not_null(item_type) VARCHAR[32]
not_null(item_id) INTEGERz
}


' relationships
' one-to-one relationship

' call_queues -> call_area : "A call queue entry is related to one area"
' user -- user_profile : "A user only \nhas one profile"
' one to may relationship
encounters --> encounter_values : "An encounter may have many encounter values"
call_queues -> call_queue_histories : "A call queue entry may have many histories"
' many to many relationship
' Add mark if you like
' user "1" --> "*" user_group : "A user may be \nin many groups"
' group "1" --> "0..N" user_group : "A group may \ncontain many users"
@enduml
```

![PlantUML diagram](http://www.plantuml.com/plantuml/png/ZPHRRnex4CVV-HHpDWzXZxZadBmXj0f2ILkfJIGKvQMfa5aFh8NNtle2sLRzxXrxWOMWIF2oS_dxD-FnY3lhc76-b9rhy2hNPOdAWIiGf5082vHw2s89jVRN1i5ReLP0iiexDB0LhW061frG3BYmbMGraUnQg8ePLWAl1DpUt7J-uRWCm6UsaDXLhCGUHvkda4jcBOG0C0j922Om7aFtkNVry32XNmfPHinjg4uTQSbXgGrKHfJCrB36K75b41Kr9hM9MQ_4Ju-KO8gJmz7ON1kCEQNTN7af3qtjK7D2TTzI62-oj_5maHto3IocOeLHh1P4qMs5UtAK-Y3meNLDypJWsCe2sp0Xmmn651-BR3mKfA2IB5-FfazVdsRPdjg3BHt3tQK4dMtCPbZqBLmfTw5Syt3PRXpPT9gIRH57977LQ3YaPr7XaGVqSiCuSRI3SFpgcpROAGH7AD4Lcjl6iOugQrTNQ3l4GkM44y5ktWzLhhqYZUr1qZglgZk1jT1s7P-AYbYXLPgayBjpF6F1K_Zo-7p_wNxM-NF6d6-OzDYIsn3nNw91Q0VScx2CxB8wXwTfeOAVTv4pAUVqs4q3HzvbbsWFp0jXdJPYnpaFNzJjCV3ZWimW2sLQvx9kDsZ2uCBHdNbXLy9XEG_RaSBBP3RzF9bzl_t_nxlyqSbVeIRjaK79N2XJYCgIhnNsdUxJvoGLf4UZXtu6Xwl12999T25cmswQ6eHj2CZ1QGZ084u8v2qQwFVZTruPlHGI8wJ9Q2LhU5K5i_7KJf0qpGLMoUhJvjfz9sm6xvSqibKRZe22RP0CLH_56tdIER_fsQvySEbJya4TcW-HfdjrsZxb9fnJtAnt_-iWnHhtWqh-I-Ajad-JPc8hettLpYlMN21DJAW67WMXPcErX9l1uF4S4ir08KIkbMDxJX0IvWuLzwNy2m00)