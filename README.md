# Sponsor-test
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Redirecting...</title>
  <script>
    // Array of sponsor URLs and their durations (in minutes)
    const sponsors = [
      { url: "https://www.mlb.com/", duration: 10 },
      { url: "https://atlanticleague.com/", duration: 10 },
      { url: "https://youtu.be/rMLYM_ZVu-4?si=sAvUj-oxKFcRPCV0", duration: 10 }
    ];

    // Get the current time in minutes since midnight
    const now = new Date();
    const minutesSinceMidnight = now.getHours() * 60 + now.getMinutes();

    // Total cycle length
    const totalCycle = sponsors.reduce((sum, sponsor) => sum + sponsor.duration, 0);

    // Figure out where we are in the rotation
    const currentCycleMinute = minutesSinceMidnight % totalCycle;

    // Determine which sponsor to redirect to
    let accumulated = 0;
    for (let sponsor of sponsors) {
      accumulated += sponsor.duration;
      if (currentCycleMinute < accumulated) {
        window.location.href = sponsor.url;
        break;
      }
    }
  </script>
</head>
<body>
  <p>Redirecting to sponsor...</p>
</body>
</html>

