# Assignment-2
import numpy as np

temps = np.array([
    [30, 32, 31, 29, 28, 27, 26],   # City A
    [22, 21, 23, 24, 25, 26, 24],   # City B
    [15, 17, 16, 18, 19, 20, 21]    # City C
])

print("Max temp City A:", temps[0].max())
print("Highest temp:", temps.max(), "on Day", np.argmax(temps) % temps.shape[1] + 1)
print("Warmer city:", "A" if temps[0].mean() > temps[1].mean() else "B")


data = {
    "st-1":{"Maths":85,"Urdu":70,"Sindhi":40,"Chemistry":90,"Physics":60},
    "st-2":{"Maths":70,"Urdu":75,"Sindhi":40,"Chemistry":90,"Physics":60},
    "st-3":{"Maths":80,"Urdu":70,"Sindhi":95,"Chemistry":90,"Physics":60},
    "st-4":{"Maths":80,"Urdu":70,"Sindhi":50,"Chemistry":85,"Physics":60},
    "st-5":{"Maths":80,"Urdu":75,"Sindhi":40,"Chemistry":90,"Physics":60}
}

for subj in data["st-1"]:
    scores = {s: m[subj] for s, m in data.items()}
    print(subj, "Max:", max(scores, key=scores.get), max(scores.values()),
          "Min:", min(scores, key=scores.get), min(scores.values()))

for s, m in data.items():
    print(s, "Max:", max(m, key=m.get), m[max(m, key=m.get)],
          "Min:", min(m, key=m.get), m[min(m, key=m.get)])

totals = {s: sum(m.values()) for s, m in data.items()}
for i, (s, t) in enumerate(sorted(totals.items(), key=lambda x: x[1], reverse=True), 1):
    print("Rank", i, ":", s, t)
