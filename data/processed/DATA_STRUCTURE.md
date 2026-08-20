# Cấu trúc dữ liệu World Cup (data/processed)

## CSV (`data/processed/csv`)

### matches.csv — 104 dòng, 17 cột
`match_id`, `date`, `kickoff_time_utc`, `stage_id`, `venue_id`, `home_team_id`, `away_team_id`, `home_score`, `away_score`, `home_penalty_score`, `away_penalty_score`, `status`, `result_type`, `home_xg`, `away_xg`, `referee_id`, `player_of_the_match_id`

### matches_detailed.csv — 104 dòng, 23 cột
`match_id`, `date`, `kickoff_time_utc`, `stage_name`, `stadium_name`, `city`, `country`, `home_team_name`, `home_fifa_code`, `away_team_name`, `away_fifa_code`, `home_score`, `away_score`, `home_penalty_score`, `away_penalty_score`, `status`, `result_type`, `home_xg`, `away_xg`, `home_goalkeeper`, `away_goalkeeper`, `player_of_the_match_name`, `referee_name`

### match_events.csv — 601 dòng, 6 cột
`event_id`, `match_id`, `minute`, `event_type`, `team_id`, `player_id`

### match_lineups.csv — 5408 dòng, 7 cột
`lineup_id`, `match_id`, `player_id`, `team_id`, `is_starting_xi`, `tactical_position`, `minutes_played`

### match_team_stats.csv — 208 dòng, 12 cột
`match_id`, `team_id`, `possession_pct`, `total_shots`, `shots_on_target`, `corners`, `fouls`, `offsides`, `saves`, `player_of_the_match`, `data_source`, `last_updated`

### match_prediction_features.csv — 104 dòng, 66 cột
Thông tin trận đấu + 60 feature đầu vào + 6 nhãn (`home_score`, `away_score`, `result_type`, `home_xg`, `away_xg`, `match_result`)

### match_prediction_features_X.csv — 104 dòng, 60 cột
Tập feature (X) cho mô hình dự đoán, gồm:
- Metadata trận: `match_id`, `date`, `kickoff_time_utc`, `stage_id`, `is_knockout`, id/tên/Mã FIFA/liên đoàn của 2 đội
- Sân & trọng tài: `venue_*`, `referee_*`
- Sức mạnh đội: `home/away_fifa_rank`, `home/away_elo`, `home/away_is_host`
- Đội hình: `home/away_squad_avg_age`, `total_caps`, `total_value_eur`, `avg_value_eur`
- Thống kê lịch sử trung bình trước giải (`home/away_prev_avg_*`): goals, possession, shots, shots_on_target, saves, corners, fouls, offsides, xg_scored, xg_conceded

### match_prediction_targets_y.csv — 104 dòng, 7 cột
Nhãn (y): `match_id`, `home_score`, `away_score`, `result_type`, `home_xg`, `away_xg`, `match_result`

### player_stats.csv — 1248 dòng, 21 cột
`player_id`, `player_name`, `team_id`, `position`, `matches_played`, `matches_started`, `minutes_played`, `goals`, `assists`, `shots`, `shots_on_target`, `yellow_cards`, `red_cards`, `penalty_goals`, `own_goals`, `clean_sheets`, `saves`, `goals_conceded`, `average_rating`, `data_source`, `last_verified`

### squads_and_players.csv — 1248 dòng, 10 cột
`player_id`, `team_id`, `player_name`, `position`, `club_team`, `market_value_eur`, `caps`, `date_of_birth`, `height_cm`, `goals`

### teams.csv — 48 dòng, 8 cột
`team_id`, `team_name`, `fifa_code`, `group_letter`, `confederation`, `fifa_ranking_pre_tournament`, `elo_rating`, `manager_name`

### tournament_stages.csv — 7 dòng, 3 cột
`stage_id`, `stage_name`, `is_knockout`

### venues.csv — 16 dòng, 8 cột
`venue_id`, `stadium_name`, `city`, `country`, `capacity`, `latitude`, `longitude`, `elevation_meters`

## JSON (`data/processed/json`)

### real_match_details.json — 104 phần tử
List các dict, khóa của mỗi phần tử: `match_id`, `home_team`, `away_team`, `home_score`, `away_score`, `home_goals`, `away_goals`

## Ghi chú
- Số trận đấu: 104 (mỗi trận có 2 đội → 208 dòng `match_team_stats`)
- 48 đội tuyển, 16 sân vận động, 7 vòng đấu
- 1248 cầu thủ (`player_stats` = `squads_and_players`)
- `match_prediction_features` = `features_X` + `targets_y` (ghép theo `match_id`)