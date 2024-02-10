VAR Filteredtable
CALCULATETABLE(
    VALUES(
        'Eligibility_History II'),
        'Eligibility_History II' [HistoryIIDateKey] IN {"19012024", "18012024", "10012024", "09012024", "08012024", "05012024", "03012024", "29122023", "28122023","27122023","22122023","21122023","20122023","19122023","15122023","13122023","08122023","07122023","05122023","30112023","29112023","28112023"},
        'Eligibility_History II'[type]= 0,
        'Eligibility_History II'[info.changes.stage.old] = "New" &&
        'Eligibility_History II'[info.changes.stage.new] = "Enrolment Attempt 1",
        
        )

VAR event_type =  'Eligibility_Events'[event_type]      
VAR event_stage = 'Eligibility_Events'[event_stage]
VAR event_created = 'Eligibility_Events'[EventsCreatedDateKey]





       Call Attempt = 
VAr current_update_id = 'Eligibility_History II'[id]
VAR current_pid = 'Eligibility_History II'[eligibility_patient]
var old_update_id = CALCULATE(MAX('Eligibility_History II'[id]), FILTER('Eligibility_History II', 'Eligibility_History II'[eligibility_patient] = current_pid && 'Eligibility_History II'[id] < current_update_id ))
VAR prev_attempt = LOOKUPVALUE( 'Eligibility_History II'[info.changes.stage.new], 'Eligibility_History II'[id], old_update_id)

return 
IF('Eligibility_History II'[type]=0, 
SWITCH(TRUE(), 
'Eligibility_History II'[info.changes.stage.new] = "Enrolment Attempt 1", "Enrolment Attempt 1",
'Eligibility_History II'[info.changes.stage.new] = "Completed" && 'Eligibility_History II'[info.changes.stage.old] = "New", "Enrolment Attempt 1",
'Eligibility_History II'[info.changes.stage.new] = "Completed - Patient Rejected HB Device" && 'Eligibility_History II'[info.changes.stage.old] = "New", "Enrolment Attempt 1",
'Eligibility_History II'[info.changes.stage.new] = "Completed - Not Able To Reach" && 'Eligibility_History II'[info.changes.stage.old] = "New", "Enrolment Attempt 1",

'Eligibility_History II'[info.changes.stage.new] = "Enrolment Attempt 2", "Enrolment Attempt 2",
'Eligibility_History II'[info.changes.stage.new] = "Completed" && 'Eligibility_History II'[info.changes.stage.old] = "Enrolment Attempt 1", "Enrolment Attempt 2",
'Eligibility_History II'[info.changes.stage.new] = "Completed - Patient Rejected HB Device" && 'Eligibility_History II'[info.changes.stage.old] = "Enrolment Attempt 1", "Enrolment Attempt 2",

'Eligibility_History II'[info.changes.stage.new] = "Enrolment Attempt 3", "Enrolment Attempt 3",
'Eligibility_History II'[info.changes.stage.new] = "Completed" && 'Eligibility_History II'[info.changes.stage.old] = "Enrolment Attempt 2", "Enrolment Attempt 3",
'Eligibility_History II'[info.changes.stage.new] = "Completed - Patient Rejected HB Device" && 'Eligibility_History II'[info.changes.stage.old] = "Enrolment Attempt 2", "Enrolment Attempt 3",
'Eligibility_History II'[info.changes.stage.new] = "Completed - Not Able To Reach" && 'Eligibility_History II'[info.changes.stage.old] = "Enrolment Attempt 2", "Enrolment Attempt 3",
'Eligibility_History II'[info.changes.stage.new] = "Completed - Patient Rejected HB Device" && 'Eligibility_History II'[info.changes.stage.old] = "Completed - Patient Rejected HB Device", "Enrolment Attempt 3",

'Eligibility_History II'[info.changes.stage.new] = "Enrolment Attempt 4", "Enrolment Attempt 4",
'Eligibility_History II'[info.changes.stage.new] = "Completed" && 'Eligibility_History II'[info.changes.stage.old] = "Enrolment Attempt 3", "Enrolment Attempt 4",
'Eligibility_History II'[info.changes.stage.new] = "Completed - Patient Rejected HB Device" && 'Eligibility_History II'[info.changes.stage.old] = "Enrolment Attempt 3", "Enrolment Attempt 4",
'Eligibility_History II'[info.changes.stage.new] = "Completed - Not Able To Reach" && 'Eligibility_History II'[info.changes.stage.old] = "Enrolment Attempt 3", "Enrolment Attempt 4",

'Eligibility_History II'[info.changes.stage.new] = "Completed" && 'Eligibility_History II'[info.changes.stage.old] = "Completed - Not Able To Reach", "Enrolment Attempt 3",
'Eligibility_History II'[info.changes.stage.new] = "Completed - Patient Rejected HB Device" && 'Eligibility_History II'[info.changes.stage.old] = "Completed - Not Able To Reach", "Enrolment Attempt 3",
'Eligibility_History II'[info.reason] = "Enrol event marked as COMPLETED by the system" && prev_attempt = BLANK(), "Enrolment Attempt 1",
'Eligibility_History II'[info.reason] = "Enrol event marked as COMPLETED by the system" && prev_attempt = "New", "Enrolment Attempt 1",
'Eligibility_History II'[info.reason] = "Enrol event marked as COMPLETED by the system" && prev_attempt = "Enrolment Attempt 1", "Enrolment Attempt 2",
'Eligibility_History II'[info.reason] = "Enrol event marked as COMPLETED by the system" && prev_attempt = "Enrolment Attempt 2", "Enrolment Attempt 3",
'Eligibility_History II'[info.reason] = "Enrol event marked as COMPLETED by the system" && prev_attempt = "Completed - Patient Rejected HB Device", "Enrolment Attempt 3",
'Eligibility_History II'[info.reason] = "Enrol event marked as COMPLETED by the system" && prev_attempt = "Completed - Not Able To Reach", "Enrolment Attempt 4"
), IF(
    'Eligibility_History II'[type]=3, SWITCH(TRUE(),
    'Eligibility_History II'[info.changes.stage.new] = "Termination Attempt 1", "Termination Attempt 1",
    'Eligibility_History II'[info.changes.stage.new] = "Termination Attempt 1" && 'Eligibility_History II'[info.changes.stage.old] = "New", "Termination Attempt 1",
    'Eligibility_History II'[info.changes.stage.new] = "Termination Attempt 2" && 'Eligibility_History II'[info.changes.stage.old] = "Termination Attempt 1", "Termination Attempt 2",
    'Eligibility_History II'[info.changes.stage.new] = "Completed" && 'Eligibility_History II'[info.changes.stage.old] = "Termination Attempt 2", "Termination Attempt 2",
    'Eligibility_History II'[info.changes.stage.new] = "Completed" && 'Eligibility_History II'[info.changes.stage.old] = "New", "Termination Attempt 1"
)))

#Call Attempts 1 = CALCULATE(DISTINCTCOUNT('Eligibility_History II'[id]), 'Eligibility_History II'[Call Attempt] =  "Enrolment Attempt 1") 

#Connected Calls = [#Total Calls] - [#No Answer Calls]

#Total Calls = [#Call Attempts 1] + [#Call Attempts 2] + [#Call Attempts 3]



% Answer rate (SMS) II =
VAR filter_SMS_sent_events = 
CALCULATETABLE('Eligibility_History II', 'Eligibility_History II'[type] = 0,
        'Eligibility_History II'[info.changes.stage.old] = "New" &&
        'Eligibility_History II'[info.changes.stage.new] = "Enrolment Attempt 1")
    
VAR filtered_table_date = 
    FILTER(
        'Eligibility_History II', 
        'Eligibility_History II'[Call Date] IN {"19012024", "18012024", "10012024", "09012024", "08012024", "05012024", "03012024", "29122023", "28122023","27122023","22122023","21122023","20122023","19122023","15122023","13122023","08122023","07122023","05122023","30112023","29112023","28112023"}
    )
VAR total_calls_made = 
    CALCULATE(
        [#Total Calls],
        filtered_table_date
    )
VAR total_calls_answered_SMS =
    CALCULATE(
        COUNTROWS(
            'Eligibility_History II'),
            'Eligibility_History II'[eligibility_event] IN filter_SMS_sent_events,
             filtered_table_date,  
            'Eligibility_History II'[type] = 0,
        'Eligibility_History II'[info.changes.stage.old] = "New" &&
        'Eligibility_History II'[info.changes.stage.new] = "Enrolment Attempt 1"
    )
RETURN 
    DIVIDE(total_calls_answered_SMS, total_calls_made)



    