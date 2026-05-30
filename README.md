# Kindle-Dashboard

A single-page web application designed and optimized for the Amazon Kindle's experimental browser. 

## Features
- **Real-Time Clock**: Big, clear digital time and date display.
- **Pomodoro Timer**: Built-in timer with basic controls to help boost your productivity.
- **Dynamic Islamic Prayer Times**: Fetches accurate prayer times via the Aladhan API, complete with a setup screen for selecting your country and city.
- **Salat Remaining Time**: A live countdown/count-up timer displayed alongside the clock. Shows how much time remains until the next Azan, or how long ago the Azan was called. After the per-prayer iqama window expires, the timer automatically jumps forward to count down to the next prayer.
- **E-ink Optimized Design**: A clean, high-contrast (black & white), and large-font UI. Built using plain HTML, CSS, and Vanilla JavaScript to ensure compatibility with older Kindle browsers without needing heavy libraries or complex animations.

## Salat Timer — Per-Prayer Iqama Windows

The timer uses a configurable `IQAMA_LIMITS` object (in minutes) to decide when to switch from showing time-since-Azan to counting down to the next prayer:

| Prayer | Iqama Window |
|---------|-------------|
| Fajr | 20 min |
| Sunrise | 45 min |
| Dhuhr | 15 min |
| Asr | 15 min |
| Maghrib | 8 min |
| Isha | 15 min |

**Timer behavior:**
- **Before Azan** → `00:MM:SS` countdown to next prayer
- **After Azan, within window** → `-00:MM:SS` count-up (time since Azan)
- **After iqama window expires** → jumps to `HH:MM:SS` countdown to the next prayer

To customize the windows for your local masjid, edit the `IQAMA_LIMITS` object near the top of the script in `index.html`:

```js
var IQAMA_LIMITS = {
    Fajr:    20,
    Sunrise: 45,
    Dhuhr:   15,
    Asr:     15,
    Maghrib:  8,
    Isha:    15
};
```
