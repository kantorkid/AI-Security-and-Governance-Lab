# Dataset

This project uses the **UTKFace** dataset.

## Details

| Attribute | Value |
|-----------|-------|
| Source | University of Tennessee, Knoxville |
| Official URL | https://susanqq.github.io/UTKFace/ |
| Total Images | 23,708 facial images |
| Format | .jpg |
| License | Research purposes only |

## Filename Format

```
AGE_GENDER_RACE_DATE.jpg
```

| Label | Values |
|-------|--------|
| Gender | 0 = Female, 1 = Male |
| Race | 0 = White, 1 = Black, 2 = Asian, 3 = Indian, 4 = Other |

## Demographics

| Race | Count | % |
|------|-------|---|
| White | 10,078 | 42.5% |
| Black | 4,526 | 19.1% |
| Indian | 3,975 | 16.8% |
| Asian | 3,434 | 14.5% |
| Other | 1,692 | 7.1% |

| Gender | Count | % |
|--------|-------|---|
| Female | 12,391 | 52.3% |
| Male | 11,314 | 47.7% |

## Setup

Raw images are not included in this repository.

1. Download UTKFace from https://susanqq.github.io/UTKFace/
2. Place all `.jpg` images in this `/data` folder
3. Update `DATA_DIR` in the notebook before running

## Governance Note

White subjects are overrepresented at 42.5% of the dataset. This imbalance is a documented risk factor analyzed in the fairness assessment and directly contributes to disparate model performance across racial groups.
