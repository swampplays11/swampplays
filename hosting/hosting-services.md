---
description: A guide on deploying applications using popular hosting methods.
---

# Hosting Services

Here is a guide on popular hosts, that I have had a good experience with, and that I recommend.

## Deploy on Heroku

Heroku is an option that I personally use to host some of my apps for free.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Advantages</th>
      <th style="text-align:left">Disadvantages</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Free to use.</li>
          <li>Trusted by many people.</li>
          <li>Decent uptime.</li>
          <li>Apps sleep after a short period of time.</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Requires credit card verification for 24/7 hosting.</li>
          <li>Can charge money, if you go over the dyno hour limits.</li>
          <li>Apps sleep after a short period of time, without <a href="internal-pinging.md">internal pinging</a>.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

{% embed url="https://heroku.com" caption="" %}

## Deploy on DigitalOcean

DigitalOcean is a very reliable service with viable security. I personally use it for my major projects \(2PG, DBots, codea.live etc.\). It costs money, but hosts apps 24/7, without extra challenges. As of writing this, I have not experienced any notable downtime, even with &gt;2 years of service.

<table>
  <thead>
    <tr>
      <th style="text-align:left">Advantages</th>
      <th style="text-align:left">Disadvantages</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left">
        <ul>
          <li>Online 24/7.</li>
          <li>Trusted by many people.</li>
          <li>Very decent uptime.</li>
          <li>Flexible pricing plans.</li>
          <li>SSH key security.</li>
        </ul>
      </td>
      <td style="text-align:left">
        <ul>
          <li>Takes a while to setup.</li>
          <li>May require Linux expertise, if you run into issues.</li>
          <li>Expensive, and initial price excludes tax.</li>
        </ul>
      </td>
    </tr>
  </tbody>
</table>

{% embed url="https://m.do.co/c/be464b522714" caption="\"Try DigitalOcean with a $100 credit\"" %}

## What about other hosting services?

There are many hosting services, however I will only recommend the ones I have had a great experience with, and I hope you will too.

