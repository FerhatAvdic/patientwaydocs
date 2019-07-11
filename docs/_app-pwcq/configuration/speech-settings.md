---
layout: section-page
title:  "Speech-settings"
section: 01-01-03
tags: configuration
---

# Speech Settigns

## PCQ Announcements

```yaml
pwhub:
  say:
    gender: female # female, male
    text_type: ssml # plain, ssmd, ssml
    name: # see list
    
call_queue:
	say_message:
		summoned:
			en: # ssml, ssmd or plain text with PatientWay expressions expanded
```



[Google SSML Reference](https://developers.google.com/actions/reference/ssml) | [Amazon Polly SSML Reference](https://docs.aws.amazon.com/polly/latest/dg/supported-ssml.html)

## General Tags

```xml
<break time="0.5s"/>
```



```
<prosody rate="medium">
```



<say-as interpret-as="characters">
<say-as interpret-as="cardinal">57 # fifty seven
<say-as interpret-as="ordinal">57 # fifty seventh
<say-as interpret-as="digits">57 # five seven

## 

## Google Specific tags

```xml
<audio clipEnd="1.75s" src="https://service.patientway.com/nextcloud/index.php/s/2xSi4xjDaX2Z9OG/download"></audio>
```



<say-as interpret-as="characters">

<say-as interpret-as="ordinal">

<say-as interpret-as="digits">