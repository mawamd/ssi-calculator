
def get_insulin_doses(slide_scale):
    correction_factor = float(slide_scale.split(":")[0])
    glucose_drop = int(slide_scale.split(":")[1].split(">")[0])
    start_of_insulin_doses = int(slide_scale.split(">")[1])

    lower_limit = start_of_insulin_doses - glucose_drop
    upper_limit = lower_limit + glucose_drop
    glucose_ranges = [lower_limit]
    insulin_doses = [0]

    while upper_limit <= 400:
        glucose_ranges.append(upper_limit)
        upper_limit += glucose_drop
        if upper_limit > start_of_insulin_doses:
            insulin_doses.append(insulin_doses[-1] + correction_factor)
        else:
            insulin_doses.append(0)

    return glucose_ranges, insulin_doses

slide_scale = input("Enter sliding scale here: ")
glucose_ranges, insulin_doses = get_insulin_doses(slide_scale)

for i in range(len(insulin_doses)):
    insulin_doses[i] = float(insulin_doses[i])
    if i == len(insulin_doses) - 1:
        print(f"{int(glucose_ranges[i])}-400 : {int(insulin_doses[i]) if insulin_doses[i].is_integer() else insulin_doses[i]} units")
    else:
        print(f"{int(glucose_ranges[i])}-{int(glucose_ranges[i+1])} : {int(insulin_doses[i]) if insulin_doses[i].is_integer() else insulin_doses[i]} units")
