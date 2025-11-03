#Assignment 8 for Programming for Psychologists

Here is my new code for displaying average earnings and number of times they selected the more delayed versus less-delayed option:

```python
data['money_chosen']= np.nan
data.loc[data['choice'] == 1,'money_chosen'] = data['money_left']
data.loc[data['choice'] == 2,'money_chosen'] = data['money_right']
data

for participant in range(1, 3):
    valid_money_chosen = data[data['participant'] == participant]['money_chosen'].dropna()
    average_money = valid_money_chosen.mean()
    print(f"Participant {participant}'s average money chosen: {average_money:.2f}")
    for x in [1,0]:
        delayed_chosen = len(data[(data['participant'] == participant) & (data['delayed_opt_chose'] == x)])
        if x == 1:
            print(f"Participant {participant} chose {delayed_chosen} number of more-delayed option")
        else:
            print(f"Participant {participant} chose {delayed_chosen} number of less-delayed option")
